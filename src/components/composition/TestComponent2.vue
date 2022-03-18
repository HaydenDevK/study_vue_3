<template>
  <h3>[ ref, reactive, toRefs 복습 ]</h3>
  <h4>-</h4>
  <div>userName : {{ userName }}</div>
  <button @click="changeName">ChangeName</button>

  <h4>-</h4>
  <div>상품명 : {{ name }}</div>
  <div>가격 : {{ price }}</div>
  <button @click="changeProduct">changeProduct</button>

  <h3>[ v-model ]</h3>
  <h4>- ref 없이 반응성이 주입되지 않으면, 변경사항이 반영되지 않는다.</h4>
  <!--
    Q. 변경사항 반영되지 않는 건 맞는데,
    changeProduct나 changeName를 실행하면 이 때 반영된다.
    어.. methods니까 컴포넌트 내 다른 data라도 변경되면 즉 updated hook이 실행되면 업데이트되는 건가...?
    test 중인데, updated hook이 실행되는 건 맞고, 근데 noRef 콘솔에 찍어보니까 변경 안되는데? 뭐지?
    반드시 파악해야겠다.
    반영이 안된다고 생각해서, 안되길 바래서 그렇게 코딩했는데, 아직 이유는 모르겠지만 의도치 않게 반영이 되고 있는 거잖아?
    methods 특성인 updated hook이 관련있는건지 없는건지
  -->
  <div>{{ noRef }}</div>
  <input type="text" v-model="noRef" />

  <h4>- ref로 반응성을 주입하면, 변경사항이 반영된다.</h4>
  <div>{{ yesRef }}</div>
  <input type="text" v-model="yesRef" />
</template>

<script>
import { ref, reactive, toRefs } from 'vue';
import { onMounted, onBeforeUpdate, onUpdated } from 'vue';
export default {
  name: 'TestComponent2',
  setup() {
    const userName = ref('Sophie');
    const changeName = function () {
      userName.value = 'SophieChanged';
    };

    const state = reactive({
      name: '티비',
      price: 100
    });
    const changeProduct = function () {
      state.name = '냉장고';
      state.price = 50;
    };

    const noRef = 'noRef';
    const yesRef = ref('yesRef');

    onBeforeUpdate(() => {
      console.log('onBeforeUpdate');
      console.log(noRef);
    });
    onUpdated(() => {
      console.log('onUpdated');
      console.log(noRef);
    });
    onMounted(() => {
      console.log('onMounted');
      console.log(noRef);
    });

    console.log(noRef);
    return {
      userName,
      changeName,
      ...toRefs(state), // 이렇게 보내주면 호출 시 state. 생략해도된다.
      changeProduct,
      noRef,
      yesRef
    };
  }
};
</script>
