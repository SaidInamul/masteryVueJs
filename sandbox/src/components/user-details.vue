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
        },
        changeName : {
            type : Function,
            required : true,
        }
    }
}
</script>

<template>
    <h1>Name : {{ name }}</h1>
    <button @click="changeName">Change Name</button>
</template>