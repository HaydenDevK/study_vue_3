<template>
  <h1>20. Refs</h1>
  <input type="text" v-model="nickName" ref="inputRef" />
  <input type="text" v-model="nickName" :style="bindingStyle" />
  <h3>[ ref vs data 바인딩 차이 ]</h3>
  <button @click="consoleRef">console ref</button><br />
  <button @click="consoleData">console data</button><br />
  <button @click="consoleThis">console this</button><br />
  <button @click="controlRef">control ref</button><br />
  <button @click="bindingStyle = { color: 'blue' }">binding style</button>
  <h4>결론 : Vue에서 돔을 직접 조작하고 싶을 때 ref 사용</h4>

  <h3>[ 비고1. ref를 쓰지 않고 DOM 조작 ]</h3>
  <button @click="consoleDataSelector($event)">
    <div>
      click =>
      <input type="text" v-model="nickName" />
    </div>
    console data selector
  </button>
  <!--
    ref :
    특정 element를 선택할 수 있는 선택자
  -->

  <h3>[ 비고2. event.currentTarget, @click.stop ]</h3>
  <button @click="consoleDataSelectorCurrent($event.currentTarget)">
    click =>
    <input type="text" v-model="nickName" />

    click =>
    <input type="text" v-model="nickName" @click.stop />
    <!--
      1. button 안에 있는 input을 눌러도 무조건 button 객체가 찍히게
      => 부모인 button에게 event.currentTarget

      2. button에 걸어둔 클릭 이벤트 함수가 자식 객체인 input에 이벤트 캡쳐링 되는 것 방지
      => 자식에게 @click.stop
    -->
  </button>

  <h3>[ ref로 자식 컴포넌트의 data, methods 사용하기 ]</h3>
  <RefsChildComp ref="childRef" />
  <button @click="consoleChildRef">child comp ref</button><br />
  <button @click="useMethodChildRef">use method child ref</button>
</template>

<script>
import RefsChildComp from '@/components/refs/RefsChildComp';
export default {
  name: 'RefsParentComp',
  components: {
    RefsChildComp
  },
  data() {
    return {
      nickName: 'nickName',
      bindingStyle: {
        color: ''
      },
      bindingFocus: true
    };
  },
  methods: {
    consoleRef() {
      console.log('inputRef :');
      console.log(this.$refs.inputRef);
    },
    consoleData() {
      console.log(this.nickName);
    },
    consoleDataSelector(event) {
      console.log(event.target);
    },
    consoleDataSelectorCurrent(eventCurrentTarget) {
      console.log(eventCurrentTarget);
    },
    consoleThis() {
      console.log(this);
    },
    controlRef() {
      this.$refs.inputRef.focus(); // focus 등은 vue에서 ref로 구현하는 게 맞는 것 같다.
      this.$refs.inputRef.style.color = 'red'; // 스타일 바인딩으로 구현 가능하지만, 그냥 ref 활용 예시
    },
    consoleChildRef() {
      console.log('childRef :');
      console.log(this.$refs.childRef);
    },
    useMethodChildRef() {
      this.$refs.childRef.sayHello(); // 자식 컴포넌트(RefsChildComp)의 함수인 sayHello를 부모 컴포넌트(RefsParentComp)에서 사용 가능하다. Q. 그런데 실무에서 이렇게 해도 될지 모르겠다?
    }
  }
};
</script>
