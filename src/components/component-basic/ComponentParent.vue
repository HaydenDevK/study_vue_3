<template>
  <h1>12. Component Basics 1</h1>
  <h3>[ 1. 정적 props String ]</h3>
  <ComponentChild PropsString="정적" />
  <h3>[ 2. 동적 props String ]</h3>
  <ComponentChild :PropsString="propsStringSecond" />
  <h3>[ 3. 동적 props Number ]</h3>
  <ComponentChild :PropsNumbers="propsNumbers" />
  <h3>[ 4. 동적 props Object ]</h3>
  <ComponentChild :PropsObject="propsObject" />
  <ComponentChild />
</template>

<script>
import ComponentChild from '@/components/component-basic/ComponentChild';

export default {
  name: 'ComponentParent',
  components: {
    ComponentChild
  },
  data() {
    return {
      propsStringSecond: '동적',
      propsNumbers: undefined, // 부모에서 넘기는 값이 undefined 즉 정의되어 있지 않아도, 자식이 정의해둔 디폴트 값이 있어서 그 값이 띄워지는 게 바람직하다.
      propsObject: {
        name: 'sophie',
        gender: 'female',
        job: 'programmer'
      }
    };
  },
  methods: {}
};
</script>
