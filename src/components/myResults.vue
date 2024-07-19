<template>
  <div class="messageDiv">
    <p>Reaction Time: {{ score }} ms</p>
    <p class="message">{{ message }}</p>
  </div>
</template>

<script>
export default {
  props: ['score'],
  data() {
    return {
      message: ''
    }
  },
  methods: {
    showResult() {
      if (this.score < 350) {
        this.message = 'Super-fast, great!.'
      } else if (this.score < 500) {
        this.message = "That's pretty good!"
      } else {
        this.message = 'Míssil R-36 enviado para sua localização.'
      }
    }
  },
  mounted() {
    this.showResult()
  }
}
</script>

<style lang="scss">
.messageDiv {
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-top: 2rem;

  p {
    display: inherit;
    justify-content: inherit;
    margin-top: 1rem;
  }
}

.message {
  color: #0faf87;
  display: flex;
  justify-content: center;
  font-weight: bold;
  font-size: 22px;
}
</style>
