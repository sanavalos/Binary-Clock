<template>
  <div>
    <BinaryValue 
      :binaryValue="formattedHour"
    />
    <BinaryValue 
      :binaryValue="formattedMinute"
    />
  </div>
</template>

<script setup>
import { onMounted, ref } from "vue"
import BinaryValue from "./BinaryValue.vue"

const BASE_BINARY = 2;
const TWELVE_HOUR = 12;

const formatCurrentHour = hour => (hour === 0 || hour === TWELVE_HOUR) ? '12' : hour < TWELVE_HOUR ? `${hour}` : `${hour - TWELVE_HOUR}`;

function convertToBinary(decimal, type) {
  if (decimal === 0) {
    switch (type) {
    case 'hour':
       return '0000'
    case 'minutes':
       return '000000'
    default:
     break;
    }
  }
  
  const binaryValues = [];

  while (decimal > 0) {
    const remainder = decimal % BASE_BINARY;
    binaryValues.unshift(remainder);
    decimal = Math.floor(decimal / BASE_BINARY);
  }

  switch (type) {
    case 'hour':
      while(binaryValues.length < 4){
        binaryValues.unshift(0)
      }
      break;
    case 'minutes':
      while(binaryValues.length < 6){
        binaryValues.unshift(0)
      }
      break;
    default:
      break;
  }
  return binaryValues.join("");
}

const formattedHour = ref();
const formattedMinute = ref();

onMounted(() => {
  setInterval(() => {
    const currentDate = new Date();
    const currentHour = currentDate.getHours();
    formattedHour.value = ref(convertToBinary(parseInt(formatCurrentHour(currentHour)), 'hour'));
    formattedMinute.value = ref(convertToBinary(currentDate.getMinutes(), 'minutes'));
  }, 1000);
});
</script>

<style scoped>

</style>
