<script setup>
import ButtonContainer from './ButtonContainer.vue'

const emits = defineEmits(['addScore'])
const props = defineProps(['score'])

const handleButtonContainerEmits = (score) => emits('addScore', score)
</script>

<template>
  <div class="card card-container">
    <p class="score-value">{{ props.score.score }}</p>

    <ButtonContainer @addScore="handleButtonContainerEmits" :score="props.score" />
  </div>
</template>

<style scoped>
.card-container {
  overflow: hidden;
}
.score-value {
  font-size: 100px;
  text-align: center;
}
</style>
