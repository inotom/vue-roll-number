<script setup lang="ts">
import { ref } from 'vue';
import RollNumber from '../components/RollNumber.vue';

const currentNumber = ref(new Date().getTime().toString());

const startAnim = () => {
  currentNumber.value = new Date().getTime().toString();
};
</script>

<template>
  <div>
    update number:
    <br>
    <roll-number :number-value="currentNumber" />
    <br>
    <input type="button" @click="startAnim" value="Update Number">
  </div>
</template>
