<template>
  <h1>14. Component Basics 3 : provide, inject</h1>

  <h3>[ ]</h3>
  <h4>CompLevel1</h4>
  <CompLevel2 />
</template>

<script>
import CompLevel2 from '@/components/provide-inject/CompLevel2';

export default {
  name: 'CompLevel1',
  components: {
    CompLevel2
  },
  data() {
    return {
      userName: 'sophie'
    };
  },
  provide() {
    return {
      userNameProvide: this.userName
      // 보내는 이름을 원래 이름과 다르게 지정해야한다.
    };
  }
};
</script>
