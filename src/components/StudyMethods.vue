<template>
  <h1>7. Methods</h1>
  <div>현재 나이 : {{ age }}</div>
  <div>5년 뒤 나이 : {{ add(5) }}</div>
  <div>10년 뒤 나이 : {{ add(10) }}</div>
</template>

<script>
export default {
  name: 'StudyMethods',
  data() {
    return {
      age: 30
    };
  },
  methods: {
    // add: () => {
    //   console.log(this); // undefined
    // }
    add(num) {
      console.log(this); // Vue 내부에서 this는 Vue 인스턴스에 바인딩된다?? Proxy
      return this.age + num;
    },
    multiply(num1, num2 = 10) {
      // num2가 매개변수로 넘어오지 않을 경우, default 10
      return num1 * num2;
    },
    squared(num) {
      return this.multiply(num, num); // 곱하기 함수를 활용한 제곱 함수
    }
  }
};
</script>
