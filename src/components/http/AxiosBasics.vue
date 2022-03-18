<template>
  <h1>18. HTTP Request</h1>
  <h3>[ axios GET (수신 및 바인딩) ]</h3>
  <button @click="getTodoList">Request Todo</button>
  <ul>
    <li v-for="todo in todolist" :key="todo.id">{{ todo.title }}</li>
  </ul>
  <div v-if="errorMessage">{{ errorMessage }}</div>
  <!-- 
    Q.어짜피 '' 빈 스트링이라 height가 안잡혀서 안보이는데 왜 v-if 처리를 해줘야할까?
    => 이를테면 CSS 상에 이 엘리먼트가 이미 min-height값이 설정된 경우를 상정해서 테스트했고, 이런 경우 필요하겠다고 납득했다.
  -->

  <h3>[ axios POST (전송) ]</h3>
  <div>
    <label for="todo">할 일</label>
    <input type="text" v-model="todoItem.title" />
    <!--
      Q. 한글 텍스트 바인딩인데, v-model 정상 작동하는 이유?
      =>
      한글 텍스트를 실시간 바인딩할 경우에만 
      :value="한글텍스트데이터" @input="한글텍스트데이터 = $event.target.value"
      실시간 바인딩이 아니라서 v-model 사용 가능 한듯?
    -->
    <button @click="createTodo">새로운 투두 생성 및 전송</button>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'AxiosBasics',
  data() {
    return {
      todoItem: {
        title: '',
        completed: 'false'
      },
      todolist: [],
      errorMessage: ''
    };
  },
  methods: {
    getTodoList() {
      const url = 'https://jsonplaceholder.typicode.com/todos';
      axios
        .get(url)
        .then((response) => {
          response.status === 200
            ? (this.todolist = response.data) // request success
            : console.log(response.status); // request failed with other status code ?
        })
        .catch((error) => {
          // request failed with status code 404 예외처리
          this.errorMessage = error;
        });
    },
    createTodo() {
      const url = 'https://jsonplaceholder.typicode.com/todos';
      axios
        .post(url, this.todoItem)
        .then((response) => {
          console.log(response);
        })
        .catch((error) => {
          console.log(error);
        });
    }
  }
};
</script>
<style scoped>
div {
  background: lightblue;
  min-height: 20px;
}
</style>
