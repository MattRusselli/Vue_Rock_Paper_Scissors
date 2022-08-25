<template>
  <div id="app">
    <h1 class="title">Rock, Paper, Scissors Says? </h1>
    <div class="scoreboard">
      <h2 class="score_text">ScoreBoard</h2>
      <div class="scorecontainer">
        <div class="float-child">
          <div class="player">
            <h3>You</h3>
            <h3 class="score">{{ playerScore }}</h3>
          </div>
        </div>
        <div class="float-child">
          <div class="computer">
            <h3>Computer</h3>
            <h3 class="score">{{ compScore }}</h3>
          </div>
        </div>
        <div class="float-child">
          <div class="tie">
            <h3>Tie</h3>
            <h3 class="score">{{ tieScore }}</h3>
          </div>
        </div>
      </div>
    </div>
    <div class="flex-row buttons">
      <button class="flex-item" v-for="choice in playerChoices" :key="choice.id" :disabled="playerChoice"
        @click="selectChoice(choice)">
        <img :src="choice.image" />
        <h4>{{ choice.label }}</h4>
      </button>
    </div>
    <div class="winner-circle flex-row" v-if="winner">
      <div class="flex-item">
        <h4>Player Chose</h4>
        <img :src="playerChoice.image" />
      </div>
      <div class="winning">
        {{ winner }}
        <div>
          <button @click="resetGame()">Restart</button>
        </div>
      </div>
      <div class="flex-item">
        <h4>Computer Chose</h4>
        <img :src="compChoice.image" />
      </div>


    </div>
  </div>
</template>

<script>
import choices from './choices'
export default {
  name: 'App',
  components: {},
  data: () => ({
    playerChoices: choices,
    playerChoice: null,
    compChoice: null,
    playerScore: 0,
    compScore: 0,
    tieScore: 0,
    winner: ''
  }),
  methods: {
    async selectChoice(value) {
      this.playerChoice = value
      this.compChoice = this.playerChoices[Math.floor(Math.random() * 3)]
      this.checkWinner()
      setTimeout(() => this.resetGame, 2000)
    },


    checkWinner() {
      if (this.playerChoice.value === this.compChoice.value) {
        this.tieScore++
        this.winner = "It's a draw!"
      } else if (this.playerChoice.value === "rock" && this.compChoice.value === "scissor") {
        this.playerScore++
        this.winner = "Player Won!"
      } else if (this.playerChoice.value === "paper" && this.compChoice.value === "rock") {
        this.playerScore++
        this.winner = "Player Won!"
      } else if (this.playerChoice.value === "scissor" && this.compChoice.value === "paper") {
        this.playerScore++
        this.winner = "Player Won!"
      } else if (this.playerChoice.value === "scissor" && this.compChoice.value === "rock") {
        this.compScore++
        this.winner = "Computer Won!"
      } else if (this.playerChoice.value === "rock" && this.compChoice.value === "paper") {
        this.compScore++
        this.winner = "Computer Won!"
      } else if (this.playerChoice.value === "paper" && this.compChoice.value === "scissor") {
        this.compScore++
        this.winner = "Computer Won!"
      }
    },
    resetGame() {
      this.winner = ''
      this.playerChoice = null
      this.compChoice = null
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Silkscreen&display=swap');

html,
body {
  background-color: #424242;
  font-family: 'Silkscreen', cursive;
  text-shadow: 4px 4px black;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #f4f6f9;
}

.flex-row {
  display: flex;
  align-items: center;
  justify-content: center;
}

.flex-item {
  font-family: 'Silkscreen', cursive;
  text-shadow: 4px 4px black;
  margin: 15px;
  padding: 1em;
  max-height: 12em;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  background-color: #272727;
  border-radius: 4px;
  border: 1px solid white;
  color: #f4f6f9;
}

button {
  border: 0;
  cursor: pointer;
  transition: all 0.3s ease;
  align-items: center;
}

button:disabled {
  cursor: not-allowed;
}

button:hover:not(:disabled) {
  opacity: 0.8;
  border: 3px solid rgba(255, 255, 255, 0.4);
}


.flex-item img {
  width: 250px;
  max-height: 8em;
  align-content: center;
  object-fit: contain;
}

.winner-circle {
  margin-top: 2em;
  border: 1px solid white;
  padding: 1em;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #272727;
}

.winner-circle button {
  padding: 1em 2em;
  border-radius: 4px;
  border: 0;
  background-color: #ffcc00;
  font-weight: 700;
}

.winner-circle button:hover {
  border: 0;
}

.scoreboard {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.scorecontainer {
  padding: 10px;
  width: 20%;
  height: 150px;
  background-color: #272727;
  border: 1px solid white;
  border-radius: 4px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.score_text {
  text-align: center;
  border-bottom: 2px solid white;
}

.float-child {
  background-color: #272727;
  width: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

h3 {
  background-color: #272727;
  text-align: center;

}

.title {
  text-shadow: 4px 4px black;
}

.winning {
  font-size: 50px;
}
</style>