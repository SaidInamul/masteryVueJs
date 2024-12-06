<script>
export default {
  data() {
    return {
      message: 'Hello vue!',
      listofNumbers: [1,2,3,4,5],
      count: 10,
      incrementAmount: 5,
      counterTitle: 'Counter Standard'
    }
  },
computed: {
    displayTitle () {
      if (this.count > 20) {
          return 'Counter Standard - Very long la'
      }
      else {
          return 'Counter Standard'
      }
    }
  },
  methods: {
    incrementCount() {
        this.count += this.incrementAmount
    },
  },
  watch: {
    count(newValue) {
      if (newValue > 20) {
          this.counterTitle += ' - Very long'
      }
    }
  }
}
</script>

<template>
  <h1>{{ displayTitle }}</h1>
  <p>{{ count }}</p>
  <button v-on:click="incrementCount">Increment</button>
  <label for="incrementAmount">Increment by: </label>
  <input
    type="number"
    v-model="incrementAmount"
  >
  <h1>{{ incrementAmount }}</h1>
  <p v-if="message.length % 2 === 0">Even: {{ message }}</p>
  <p v-else>Odd: {{ message }}</p>
  <li v-for="number in listofNumbers">{{ number*2 }}</li>
</template>