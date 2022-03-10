<template>
  <div class="wrapper">
    <div class="container">
      <h3>
        [ 자식은 prop을 수정할 수 없지만, props의 property는 수정할 수 있다. ]
      </h3>
      <div>props : {{ props }}</div>
      <div v-if="propsToData">props.key 변경 : {{ propsToData }}</div>
      <button @click="propsChange">change props</button>
      <!-- Q.
        1. 굳이 이렇게 해야할 이유가 있을까?
        2. https://kr.vuejs.org/v2/guide/components-props.html#%EB%8B%A8%EB%B0%A9%ED%96%A5-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%9D%90%EB%A6%84
        여기서 computed로 가능하다고 봤는데, 왜 에러가 나는지?
      -->

      <h3>[ 혹은 emit으로 이벤트를 전달해서, 부모가 수정하게 할 수 있다. ]</h3>
      <button @click="closeChild">close</button>

      <h3>[ 자식에서 부모로 데이터 보내기 ]</h3>
      <input v-model="userName" />
      <button @click="sendData">Send Data</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ComponentChild2',
  props: {
    displayDetail: Boolean,
    props: Object
  },
  data() {
    return {
      propsToData: this.props,
      userName: ''
    };
  },
  // computed: {
  // changePropsProperty() {
  //   return (this.propsToData.key = 'value2');
  // }
  // },
  methods: {
    propsChange() {
      this.propsToData.key = 'value2';
    },
    closeChild() {
      this.$emit('closeChild'); // closeDetail이라는 이름으로 부모에게 이벤트를 전송
    },
    sendData() {
      this.$emit('sendData', this.userName);
    }
  }
};
</script>

<style scoped>
.wrapper {
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.container {
  background: #fff;
  width: 60%;
}
</style>
