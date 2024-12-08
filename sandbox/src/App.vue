<script>
import counter from './components/counter.vue';
import userDetails from './components/user-details.vue';

export default {
  components : {
    counter, userDetails,
  },
  data() {
    return {
      message: 'Hello vue!',
      listofNumbers: [1,2,3,4,5],
      userDetails : {
        name : 'Hafiz',
        title : 'Software Engineer',
        favouriteFramework : 'VueJs',
        favouriteFood : 'Fried Chicken',
      }
    }
  },
};

</script>

<template>
  <!-- <userDetails :user="userDetails" /> -->
   <userDetails />
  <counter />
  <p v-if="message.length % 2 === 0">Even: {{ message }}</p>
  <p v-else>Odd: {{ message }}</p>
  <li v-for="number in listofNumbers">{{ number*2 }}</li>
</template> 