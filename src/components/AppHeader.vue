<script setup>
const props = defineProps(['winningTeam'])
</script>

<template>
  <h1>
    <span :class="{ 'has-text-warning': props.winningTeam.team === 'Team 1' }">Team 1</span>
    vs.
    <span :class="{ 'has-text-warning': props.winningTeam.team === 'Team 2' }">Team 2</span>
  </h1>
</template>

<style scoped>
h1 {
  color: white;
  font-size: 100px;
  font-weight: bold;
  margin-top: 30px;
}

@media (max-width: 768px) {
  h1 {
    align-items: center;
    display: flex;
    flex-direction: column;
    font-size: 60px;
  }
}
</style>
