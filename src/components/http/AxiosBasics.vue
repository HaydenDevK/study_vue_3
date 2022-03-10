<template>
  <h1>18. HTTP Requests</h1>
  <h3>[ axios ]</h3>
  <button @click="getTodoList">Request Todo</button>
  <div></div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'AxiosBasics',
  methods: {
    getTodoList() {
      const url = 'https://jsonplaceholder.typicode.com/todos';
      axios.get(url).then((response) => {
        console.log(response);
      });
    }
  }
};
</script>
