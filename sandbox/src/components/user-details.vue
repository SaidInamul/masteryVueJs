<script>
export default {
    props : {
        // user : {
        //     type : Object,
        //     required : true,
        // }
        name : {
            type : String,
            required : true,
            default : 'Jon Doe',
        },
        food : {
            type : String,
            required : true,
            default : 'Pizza',
        }
    }
}
</script>

<template>
    <!-- <h1>Name : {{ user.userName }}</h1>
    <h1>Favourite Food : {{ user.favouriteFood }}</h1> -->

    <h2>Name : {{ name }}</h2>
    <h2>Food : {{ food }}</h2>

</template>