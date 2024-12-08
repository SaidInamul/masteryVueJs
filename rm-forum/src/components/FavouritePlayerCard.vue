<script>
export default {
    props : {
        player : {
            type : Object,
            required : true,
        }
    },
    emits : [
        'favourite'
    ],
    methods : {
        favouritePlayer () {
            this.$emit("favourite", this.player)
        }
    }
}

</script>

<template>
    <div>
        <button @click="favouritePlayer">⭐️{{ player.name }}</button>
    </div>

</template>