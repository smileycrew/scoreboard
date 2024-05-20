<script setup>
import ScoreButton from './ScoreButton.vue'

const emits = defineEmits(['addScore'])
const props = defineProps(['score'])

const handleButtonEmits = (score) => emits('addScore', score)
</script>

<template>
  <div class="button-container">
    <ScoreButton :action="'-'" @addScore="handleButtonEmits" :score="props.score" />
    <ScoreButton :action="'+'" @addScore="handleButtonEmits" :score="props.score" />
  </div>
</template>

<style scoped>
.button-container {
  display: flex;
  width: 100%;
}
</style>
