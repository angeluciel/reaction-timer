<script>
import Block from './components/BlockSelect.vue'
import Result from './components/myResults.vue'

export default {
  name: 'App',
  components: { Block, Result },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.score = null
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
    },
    showResults() {}
  }
}
</script>

<template>
  <h1>Reaction Speed Timer</h1>
  <div class="buttonDiv"><button @click="start" :disabled="isPlaying">play</button></div>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Result v-if="score != null" :score="score" />
</template>

<style scoped lang="scss">
$--read-color: #797979;

.buttonDiv {
  margin: 1rem;
}

@mixin centerIt() {
  display: flex;
  justify-content: center;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #3b3b42;
  margin-top: 60px;
  @include centerIt;
  align-items: center;

  p {
    @include centerIt;
    color: $--read-color;
  }
}

p {
  display: flex;
  justify-content: center;
}
</style>
