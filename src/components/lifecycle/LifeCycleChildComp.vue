<template>
  <div style="background: lightgreen">
    <h4>child component</h4>
    <input type="text" v-model="updateTest" />
  </div>
</template>

<script>
export default {
  name: 'LifeCycleChildComp',
  data() {
    return {
      updateTest: ''
    };
  },
  beforeCreate() {
    // 컴포넌트가 created 되기 직전에
    console.log('child before create');
  },
  created() {
    // 컴포넌트가 created 된 시점에
    console.log('child created');
  },
  beforeMount() {
    // 컴포넌트가 mounted 되기 직전에
    console.log('child before mount');
  },
  mounted() {
    // 컴포넌트가 mounted(렌더링) 된 시점에 (전체 렌더링 완료 상태, 자식 컴포넌트 렌더링 완료 상태(?)는 보장하지 않음)
    console.log('child mounted');
    this.$nextTick(() => {
      // 전체 렌더링 완료된 시점에
      console.log('child nextTick mounted');
    });
  },
  beforeUpdate() {
    // 컴포넌트가 updated 되기 직전에
    console.log('child before updated');
  },
  updated() {
    // 컴포넌트가 updated 된 시점에
    console.log('child updated');
  },
  beforeUnmount() {
    // 컴포넌트가 unmounted 되기 직전에
    console.log('child before unmounted');
  },
  unmounted() {
    // 컴포넌트가 unmounted 된 시점에
    console.log('child unmounted');
  }
};
</script>
