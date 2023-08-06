<template>
  <p>{{props.binaryValue?.value}}</p>
</template>

<script setup >
import { defineProps } from 'vue'
const props = defineProps({
 binaryValue: {
  type: String,
  required: true
 }
})
</script>

<style scoped>
p{
  text-align: left;
  margin: 0 1rem;
  font-size: 10vw;
}
</style>
