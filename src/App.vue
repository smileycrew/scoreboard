<script setup>
import { computed, ref } from 'vue'
import AppHeader from './components/AppHeader.vue'
import ScoreCard from './components/ScoreCard.vue'

const scores = ref([
  {
    id: 1,
    team: 1,
    score: 0
  },
  {
    id: 2,
    team: 2,
    score: 0
  }
])

const winningTeam = computed(() => {
  const team1 = scores.value[0]
  const team2 = scores.value[1]

  if (team1.score > team2.score) {
    return {
      team: 'Team 1',
      difference: team1.score - team2.score
    }
  } else if (team2.score > team1.score) {
    return {
      team: 'Team 2',
      difference: team2.score - team1.score
    }
  } else {
    return {
      team: 'Tied'
    }
  }
})

const addScore = (score) => {
  if (score.action === '-') {
    const updateScores = scores.value.map((s) => {
      if (s.id === score.id && s.score > 0) {
        return {
          ...s,
          score: s.score - 1
        }
      }

      return s
    })

    scores.value = updateScores
  } else if (score.action === '+') {
    const updatedScores = scores.value.map((s) => {
      if (s.id === score.id) {
        return {
          ...s,
          score: s.score + 1
        }
      }

      return s
    })

    scores.value = updatedScores
  }
}
</script>

<template>
  <div class="app">
    <AppHeader :winningTeam="winningTeam" />

    <p class="match-info" v-if="winningTeam.team === 'Tied'">The game is currently tied</p>
    <p class="match-info" v-if="winningTeam.difference > 1">
      {{ winningTeam.team }} is leading by {{ winningTeam.difference }} points
    </p>
    <p class="match-info" v-if="winningTeam.difference === 1">
      {{ winningTeam.team }} is leading by {{ winningTeam.difference }} point
    </p>

    <div class="scorecards">
      <ScoreCard @addScore="addScore" :key="score.id" :score="score" v-for="score in scores" />
    </div>
  </div>
</template>

<style scoped>
.app {
  align-items: center;
  background-color: #2c3e50;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100vw;
}
.match-info {
  color: white;
}
.scorecards {
  display: flex;
  height: 100%;
  justify-content: center;
  gap: 100px;
  margin-top: 100px;
  width: 100%;
}
@media (max-width: 768px) {
  .scorecards {
    align-items: stretch;
    flex-direction: column;
    /* width: 100vw; */
  }
}
</style>
