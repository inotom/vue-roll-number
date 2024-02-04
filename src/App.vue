<script setup lang="ts">
import RollNumber from './components/RollNumber.vue';
import RollNumberController from './components/RollNumberController.vue';
</script>

<template>
  <div>
    default options:<br>
    <roll-number
      number-value="3200"
      />
  </div>

  <hr>

  <div>
    custom block name:<br>
    <roll-number
      number-value="1,980,000"
      block-name="roll-number--warn"
      />
  </div>

  <hr>

  <div>
    animation duration is 10000ms:<br>
    <roll-number
      number-value="1,920"
      :anim-duration="10000"
      />
  </div>

  <hr>

  <div>
    animation duration is 10000ms, animation interval is 100ms:<br>
    <roll-number
      number-value="3,280"
      :anim-duration="10000"
      :anim-interval="100"
      />
  </div>

  <hr>
  <div>
    <roll-number-controller />
  </div>
</template>

<style lang="scss">
.roll-number {
  font-weight: bold;
  font-size: 30px;

  $root: #{&};

  &--warn {
    @extend #{$root};
    color: #c00;
  }
}
</style>
