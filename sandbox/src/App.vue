<script>
import counter from './components/counter.vue';

export default {
  components : {
    counter,
  },
  data() {
    return {
      message: 'Hello vue!',
      listofNumbers: [1,2,3,4,5],
    }
  },
};

</script>

<template>
  <counter />
  <p v-if="message.length % 2 === 0">Even: {{ message }}</p>
  <p v-else>Odd: {{ message }}</p>
  <li v-for="number in listofNumbers">{{ number*2 }}</li>
</template> 