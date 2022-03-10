<template>
  <h1>13. Component Basics 2 : props, emit</h1>
  <button @click="displayChild = true">Display Child</button>
  <ComponentChild2
    :displayChild="displayChild"
    v-if="displayChild"
    :props="props"
    @closeChild="close"
    @sendData="showData"
  />
  <!-- 
      closeDetail라는 이벤트가 전달되어오면, close함수를 실행 
      sendData라는 이벤트가 전달되어오면, showData함수를 실행
  -->
</template>

<script>
import ComponentChild2 from '@/components/component-basic/ComponentChild2';

export default {
  name: 'ComponentParent2',
  components: {
    ComponentChild2
  },
  data() {
    return {
      displayChild: false,
      props: {
        key: 'value1'
      }
    };
  },
  methods: {
    close() {
      this.displayChild = false;
    },
    showData(data) {
      console.log(data);
    }
  }
};
</script>
