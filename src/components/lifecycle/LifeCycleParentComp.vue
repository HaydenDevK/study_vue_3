<template>
  <h1>19. LifeCycle</h1>

  <div style="background: lightpink">
    <h3>[ beforeCreate, created, beforeMount, mounted, nextTick ]</h3>
    <h4>parent component</h4>
    <LifeCycleChildComp />
    <h4>순서 정리</h4>
    <ul>
      <li>parent before create</li>
      <li>parent created</li>
      <li>parent before mount</li>
      <li>child before create</li>
      <li>child created</li>
      <li>child before mount</li>
      <li>child unmounted</li>
      <li>parent unmounted</li>
      <li>child mounted</li>
      <li>parent mounted</li>
      <li>child nextTick mounted</li>
      <li>parent nextTick mounted</li>
    </ul>

    <h3>[ beforeUpdate, updated ]</h3>
    <h4>parent component</h4>
    <input type="text" v-model="updateTest" />
    <LifeCycleChildComp />

    <h3>[ beforeUnmount, unmounted ]</h3>
    <h4>parent component</h4>
    <LifeCycleChildComp v-if="showChild" />
    <button v-if="showChild" @click="showChild = false">unmmount child</button>
    <ul>
      <li>parent before updated</li>
      <li>child before unmounted</li>
      <li>child unmounted</li>
      <li>parent updated</li>
    </ul>
  </div>
</template>

<script>
import LifeCycleChildComp from '@/components/lifecycle/LifeCycleChildComp';
export default {
  name: 'LifeCycleParentComp',
  components: {
    LifeCycleChildComp
  },
  data() {
    return {
      updateTest: '',
      showChild: true
    };
  },
  beforeCreate() {
    // 컴포넌트가 created 되기 직전에
    console.log('parent before create');
  },
  created() {
    // 컴포넌트가 created 된 시점에
    console.log('parent created');
  },
  beforeMount() {
    // 컴포넌트가 mounted(렌더링) 되기 직전에
    console.log('parent before mount');
  },
  mounted() {
    // 컴포넌트가 mounted(렌더링) 된 시점에 (전체 렌더링 완료 상태, 자식 컴포넌트 렌더링 완료 상태(?)는 보장하지 않음)
    console.log('parent mounted');
    this.$nextTick(() => {
      // 전체 렌더링, 자식 컴포넌트 렌더링(?) 완료된 시점에
      console.log('parent nextTick mounted');
    });
  },
  beforeUpdate() {
    // 컴포넌트가 updated 되기 직전에
    console.log('parent before updated');
  },
  updated() {
    // 컴포넌트가 updated 된 시점에
    console.log('parent updated');
  },
  beforeUnmount() {
    // 컴포넌트가 unmounted 되기 직전에
    console.log('parent before unmounted');
  },
  unmounted() {
    // 컴포넌트가 unmounted 된 시점에
    console.log('parent unmounted');
  }
};
</script>
<!--
  특정 element를 선택할 수 있는 선택자 ref
-->
