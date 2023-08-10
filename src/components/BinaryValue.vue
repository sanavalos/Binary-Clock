<template>
  <p>{{props.binaryValue?.value}}</p>
</template>

<script setup >
  import { defineProps } from 'vue'
  const props = defineProps({
    binaryValue: {
      type: Object,
      required: true
    }
  })
</script>

<style scoped>
  p{
    text-align: left;
    margin: 0 1rem;
    font-size: 10vw;
    animation: neon-glow-animation 1.5s ease-in-out infinite alternate;
    &:hover{
      transition: all 0.5s ease-in-out;
      font-size: 15vw;
    }
    &:not(:hover){
      transition: all 0.5s ease-in-out;
    }
  }
  @keyframes neon-glow-animation {
  from {
    text-shadow: 0;
  }
  to {
    text-shadow: 0 0 4px #00ff00, 0 0 10px #00ff00, 0 0 16px #00ff00;
  }
  to{
    text-shadow: 0 0 4px #00ff00, 0 0 10px #00ff00, 0 0 16px #00ff00;
  }
}
</style>
