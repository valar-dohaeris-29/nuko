<template>
  <div>
    <ul class="flashcard-list">
      <li v-on:click="toggleCard(card)" v-for="(card, index) in cards" v-bind:key="index">
        <transition name="flip">
          <p v-bind:key="card.flipped" class="card">
            {{ card.flipped ? card.back : card.front }}
            <span v-on:click="cards.splice(index, 1)" class="delete-card">X</span>
          </p>
        </transition>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      cards: [
        {
          front: 'Do you have a map?',
          back: 'Because I just got lost in your eyes.',
          flipped: false,
        },
        {
          front: 'Is your name Google?',
          back: 'Because you have everything I\'ve been searching for.',
          flipped: false,
        },
        {
          front: 'Do you believe in love at first sight?',
          back: 'or should I walk by again?',
          flipped: false,
        },
        {
          front: 'Are you a magician?',
          back: 'Every time I look at you, everyone else disappears.',
          flipped: false,
        },
        {
          front: 'If you were a vegetable...',
          back: 'You\'d be a cute-cumber!',
          flipped: false,
        },
      ],
      newFront: '',
      newBack: '',
      error: false
    }
  },
  methods: {
    toggleCard: function (card) {
      card.flipped = !card.flipped;
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body {
  font-family: 'Montserrat', sans-serif;
  text-align: center;
}

ul {
  padding-left: 0;
  display: flex;
  flex-flow: row wrap;
}

li {
  list-style-type: none;
  padding: 10px 10px;
  transition: all 0.3s ease;
}

.container {
  max-width: 100%;
  padding: 2em;
}

.card {
  display: block;
  width: 150px;
  height: 175px;
  padding: 80px 50px;
  background-color: #51aae5;
  border-radius: 7px;
  margin: 5px;
  text-align: center;
  line-height: 27px;
  cursor: pointer;
  position: relative;
  color: #fff;
  font-weight: 600;
  font-size: 20px;
  -webkit-box-shadow: 9px 10px 22px -8px rgba(209, 193, 209, .5);
  -moz-box-shadow: 9px 10px 22px -8px rgba(209, 193, 209, .5);
  box-shadow: 9px 10px 22px -8px rgba(209, 193, 209, .5);
  will-change: transform;
}

li:hover {
  transform: scale(1.1);
}

li:nth-child(-n+3) .card {
  background-color: #e65f51;
}

li:nth-child(2n+1) .card {
  background-color: #a17de9;
}

li:nth-child(4n) .card {
  background-color: #feca34;
}

li:nth-child(5n-2) .card {
  background-color: #51aae5;
}

li:nth-child(4n+4) .card {
  background-color: #feca34;
}

li:nth-child(-7n+7) .card {
  background-color: #e46055;
}

.delete-card {
  position: absolute;
  right: 0;
  top: 0;
  padding: 10px 15px;
  opacity: .4;
  transition: all 0.5s ease;
}

.delete-card:hover, .error {
  opacity: 1;
  transform: rotate(360deg);
}

.flip-enter-active {
  transition: all 0.4s ease;
}

.flip-leave-active {
  display: none;
}

.flip-enter, .flip-leave {
  transform: rotateY(180deg);
  opacity: 0;

}

/* Form */
.flashcard-form {
  position: relative;
}


label {
  font-weight: 400;
  color: #333;
  margin-right: 10px;
}

input {
  border-radius: 5px;
  border: 2px solid #eaeaea;
  padding: 10px;
  outline: none;
}

button {
  border-radius: 5px;
  border: 1px solid #87cb84;
  background-color: #87cb84;
  padding: 8px 15px;
  outline: none;
  font-size: 14px;
  font-weight: 700;
  color: #fff;
  cursor: pointer;
  transition: all 0.3s ease;
}

button:hover {
  background-color: #70a66f;
}

.error {
  margin-top: 10px;
  display: block;
  color: #e44e42;
  font-weight: 600;
}


</style>
