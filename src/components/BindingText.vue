<template>
  <h1>1. Text Binding : v-text, v-html</h1>
  <!-- 1. v-text : 자바스크립트의 innerText -->
  <div>{{ user.name }}님 안녕하세요</div>
  <div v-text="user.name"></div>
  <!-- v-text는 내용이 없는 태그에 사용 가능-->
  <div v-text="`${user.name}님 안녕하세요`"></div>

  <!-- 2. v-html : 자바스크립트의 innerHTML -->
  <div v-html="button"></div>
  <div v-html="buttonDanger"></div>
  <!-- v-html에 코드를 삽입해서 사용할 수도 있으므로, 보안에 유의하여 반드시 신뢰할 수 있는 데이터만 바인딩해야 한다. -->
</template>

<script>
export default {
  name: 'BindingText',
  data() {
    return {
      user: {
        name: 'user'
      },
      button: '<button>나는 눌러도 괜찮지!</button>',
      buttonDanger: `<button onclick="alert('해킹')">나는 누르면 큰일나지!</button>`
    };
  }
};
</script>
