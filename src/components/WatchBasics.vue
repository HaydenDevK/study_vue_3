<template>
  <h1>11. Watch</h1>
  <h3>[ 기초 watch ]</h3>
  <div>현재 잔액 : {{ money }}</div>
  <div>
    <button @click="money += 100">earn money</button>
    <button @click="money -= 100">spend money</button>
  </div>
  <h3>[ deep _객체 내부 프로퍼티 값(즉, 네트스된 객체까지) 변화 감지 ]</h3>
  <h4>- 틀린 예</h4>
  <div>{{ consumption1 }}</div>
  <button @click="consumption1.food += 500">buy more food</button>
  <!-- watch 실행안된다. 즉, consumption 내부 프로퍼티 변화까지 감지하지 않는다. -->
  <h4>- 맞는 예</h4>
  <div>{{ consumption2 }}</div>
  <button @click="consumption2.food += 500">buy more food</button>

  <h3>[ immediate _첫 렌더링 시에도 초기 값으로 watch 실행 ]</h3>
  <input type="text" v-model="userName" />
</template>

<script>
export default {
  name: 'WatchBasics',
  data() {
    return {
      money: 0,
      consumption1: {
        food: 3000,
        fee: 2000,
        fare: 10000
      },
      consumption2: {
        food: 3000,
        fee: 2000,
        fare: 10000
      },
      userName: 'sophie'
    };
  },
  computed: {},
  watch: {
    money(newValue, oldValue) {
      // 변경 후 현재 값, 변경 이전 값
      console.log(newValue, oldValue);
      if (newValue >= 300 && newValue > oldValue) {
        console.log('300 이상 + 상승 중');
      } else if (newValue <= 100 && oldValue > newValue) {
        console.log('100 이하 + 하락 중');
      }
    },
    consumption1(current, before) {
      console.log('총 지출액에 변화가 있습니다.', current, before);
    },
    consumption2: {
      // object 형태로 선언하고, handler와 deep 정의
      handler(current, before) {
        console.log('총 지출액에 변화가 있습니다.', current, before);
      },
      deep: true // 객체 내부 프로퍼티 값(즉, 네트스된 객체까지) 변화를 감지한다.
    },
    userName: {
      handler(current) {
        console.log('current : ', current);
      },
      immediate: true // 첫 렌더링 시에도 초기 값으로 watch가 실행된다. Q. 이렇게 해야하는 실무 사례가 궁금하다.
    }
  }
};
</script>
