<template>
  <h2>{{ customTittle }}</h2>
  <p>{{ counter }} <sub>2</sub> = {{ squareCounter }}</p>
  <div>
    <button @click="increase">+ 1</button>
    <button @click="decrease">- 1</button>
  </div>
</template>

<script>
export default {
  //props: ['tittle'],
  props: {
    tittle: String,
    start: {
      type: Number,
      default: 1,
      validator(value) {
        return value > 100
      },
    },
  },
  data() {
    return {
      counter: this.start,
    }
  },
  methods: {
    getSquareValue() {
      return this.counter * this.counter
    },
    increase() {
      this.counter++
    },
    decrease() {
      this.counter--
    },
  },
  computed: {
    squareCounter() {
      return this.counter * this.counter
    },
    customTittle() {
      return !this.tittle ? 'Counter' : this.tittle
    },
  },
}
</script>

<style>
button {
  margin: 0 5px;
  border-radius: 5px;
  background-color: #64b687;
  border: 1px solid white;
  color: white;
  cursor: pointer;
  padding: 5px 15px;
  transition: 0.3s ease-in-out;
}

button:hover {
  background-color: #5aa67b;
  transition: 0.3s ease-in-out;
}
</style>
