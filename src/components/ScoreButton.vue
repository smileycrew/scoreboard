<script setup>
const emits = defineEmits(['addScore'])
const props = defineProps(['action', 'score'])

const handleAddScore = () => emits('addScore', { ...props.score, action: props.action })
</script>

<template>
  <button
    :class="{
      'add-button': action === '+',
      'subtract-button': action === '-'
    }"
    @click="handleAddScore"
  >
    <p class="button-icon">{{ props.action }}</p>
  </button>
</template>

<style scoped>
.add-button {
  align-items: center;
  background-color: #acd793;
  border: none;
  display: flex;
  height: 100px;
  justify-content: center;
  min-width: 100px;
  width: 100%;
}
.button-icon {
  font-size: 60px;
  padding: 0;
  margin: 0;
}
.subtract-button {
  align-items: center;
  background-color: #f15a59;
  border: none;
  display: flex;
  height: 100px;
  justify-content: center;
  min-width: 100px;
  width: 100%;
}
</style>
