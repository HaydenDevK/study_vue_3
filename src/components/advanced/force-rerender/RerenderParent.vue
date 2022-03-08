<template>
  <h1>Component Force Rendering</h1>

  <h3>[ 1. key 활용 ]</h3>
  {{ key }}
  <RerenderChildKey :key="key" />
  <RerenderChildKey :key="key" />
  <RerenderChildKey :key="key" />
  <!-- 1. 자식 컴포넌트에 key를 props로 내려준다. 여기서 중요한 것! Vue는 변경된 사항과 변경되지 않은 사항을 추적할 수 있도록 key 속성을 제공한다. -->
  <!-- 
  <div>
    <h4>
      2개 이상을 같은 시점에 리렌더링하는 방법 (키는 고유해야 하기 때문에 각각
      다르게)
    </h4>
    <RerenderChildKey :key="`${key + 1}`" />
    <RerenderChildKey :key="`${key + 1}`" />
  </div> -->
  <button @click="forceRerenderKey">forceRerenderKey</button>

  <h3>[ 2. v-if 활용 ]</h3>
  <RerenderChildIf v-if="renderComponent" />
  <!--
    v-if는 조건이 true일 때만 해당 element를 렌더링하기 때문에, 
    false로 바꾸면 unmounted 즉 DOM에서 삭제되고,
    true로 다시 바꾸면 다시 렌더링되는 것을 이용 
  -->
  <button @click="forceRerenderIf">forceRerender</button>
</template>

<script>
import RerenderChildKey from '@/components/advanced/force-rerender/RerenderChildKey';
import RerenderChildIf from '@/components/advanced/force-rerender/RerenderChildIf';
export default {
  name: 'RerenderParent',
  components: {
    RerenderChildKey,
    RerenderChildIf
  },
  data() {
    return {
      key: 0,
      renderComponent: true
    };
  },
  methods: {
    forceRerenderKey() {
      // 2. 강제 ReRerendering이 필요할때 forceRerender() method를 호출
      this.key += 1;
      console.log(this.key);
      // 3. 매번 key가 올라가면서 변경되기 때문에
    },
    forceRerenderIf() {
      // Removing child component from the DOM
      this.renderComponent = false;

      this.$nextTick(() => {
        // Adding child component back in
        this.renderComponent = true;
      });
    }
  }
};
</script>
