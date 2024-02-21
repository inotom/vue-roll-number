<script setup lang="ts">
import { ref, watch } from 'vue';

interface Props {
  numberValue: string;
  animDuration?: number;
  animInterval?: number;
  blockName?: string;
}

const props = withDefaults(defineProps<Props>(), {
  animDuration: 3000,
  animInterval: 10,
  blockName: 'roll-number',
});

const isAnimation = ref(false);
const currentNumber = ref(props.numberValue);
const intervalID = ref(-1);

const initialize = () => {
  if (isAnimation.value) {
    return;
  }

  isAnimation.value = true;

  let totalTime = 0;

  intervalID.value = window.setInterval(() => {
    totalTime += props.animInterval;

    let newNumber = '';

    for (let i = 0; i < props.numberValue.length; i++) {
      if (isUpdateTime(i, totalTime)) {
        newNumber += props.numberValue[i];
      } else if (isSeparator(i)) {
        newNumber += props.numberValue[i];
      } else {
        newNumber += `${getRandomInt(0, 9)}`;
      }
    }

    currentNumber.value = newNumber;

    if (totalTime > props.animDuration) {
      window.clearInterval(intervalID.value);
      isAnimation.value = false;
    }

  }, props.animInterval)
};

const isUpdateTime = (index: number, totalTime: number): boolean => {
  const interval = props.numberValue.length;
  return props.animDuration - (props.animInterval * (index + 1) * interval) < totalTime;
};

const isSeparator = (index: number): boolean => {
  return !Number.isInteger(parseInt(props.numberValue[index], 10));
};

const getRandomInt = (min: number, max: number): number => {
  return Math.floor(Math.random() * (max - min + 1)) + min;
};

// Using getter function.
// https://ja.vuejs.org/guide/essentials/watchers#watch-source-types
watch(() => props.numberValue, (newNumber, oldNumber) => {
  if (newNumber !== oldNumber) {
    initialize();
  }
});

initialize();
</script>

<template>
  <span
    :class="blockName"
    :is-animation="isAnimation"
  >
    {{ currentNumber }}
  </span>
</template>
