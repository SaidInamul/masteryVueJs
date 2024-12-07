<script>
export default {
    data() {
        return {
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
    <h1>{{ count }}</h1>
    <h2>{{ incrementAmount }}</h2>
    <button v-on:click="incrementCount">Increment</button>
    <label for="incrementAmount">Increment by: </label>
    <input
        type="number"
        v-model="incrementAmount"
    >
    <hr>

</template>