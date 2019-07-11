<template>
  <span
    :class="blockName"
    :is-animation="isAnimation"
  >
    {{ currentNumber }}
  </span>
</template>

<script>
export default {
  props: {
    numberValue: {
      type: String,
      required: true,
    },

    animDuration: {
      type: Number,
      default: 3000,
    },

    animInterval: {
      type: Number,
      default: 10,
    },

    blockName: {
      type: String,
      default: 'roll-number',
    },
  },

  data() {
    return {
      isAnimation: false,
      currentNumber: this.numberValue,
      intervalID: -1,
    };
  },

  watch: {
    numberValue(newNumber, oldNumber) {
      if (newNumber !== oldNumber) {
        this.initialize();
      }
    },
  },

  created() {
    this.initialize();
  },

  methods: {
    initialize() {

      if (this.isAnimation) {
        return;
      }

      this.isAnimation = true;

      let totalTime = 0;

      this.intervalID = setInterval(() => {
        totalTime += this.animInterval;

        let newNumber = '';

        for (let i = 0; i < this.numberValue.length; i++) {
          if (this.isUpdateTime(i, totalTime)) {
            newNumber += this.numberValue[i];
          } else if (this.isSeparator(i)) {
            newNumber += this.numberValue[i];
          } else {
            newNumber += this.getRandomInt(0, 9) + '';
          }
        }

        this.currentNumber = newNumber;

        if (totalTime > this.animDuration) {
          clearInterval(this.intervalID);
          this.isAnimation = false;
        }

      }, this.animInterval);
    },

    isUpdateTime(index, totalTime) {
      const interval = this.numberValue.length;
      return this.animDuration - (this.animInterval * (index + 1) * interval) < totalTime;
    },

    isSeparator(index) {
      return !Number.isInteger(parseInt(this.numberValue[index], 10));
    },

    getRandomInt(min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    },
  },
};
</script>
