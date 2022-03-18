<template>
  <h3>[ life cycle ]</h3>
  <input type="text" v-model="userName" ref="inputRef" />
  <h4>- props</h4>
  <CompositionLifeCycleChild
    firstName="Sophie"
    lastName="Kim"
    @sendParent="sendParent"
  />
</template>

<script>
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  ref
} from 'vue';

import CompositionLifeCycleChild from '@/components/composition/CompositionLifeCycleChild';
export default {
  name: 'CompositionLifeCycle',
  components: {
    CompositionLifeCycleChild
  },
  setup() {
    const userName = ref('Sophie');

    const inputRef = ref(null);

    onBeforeMount(() => {
      console.log('onBeforeMount');
    });
    onMounted(() => {
      console.log('onMounted');
      inputRef.value.focus();
    });
    onBeforeUpdate(() => {
      console.log('onBeforeUpdate');
    });
    onUpdated(() => {
      console.log('onUpdated');
    });
    onBeforeUnmount(() => {
      console.log('onBeforeUnmount');
    });
    onUnmounted(() => {
      console.log('onUnmounted');
    });

    return {
      userName,
      inputRef
    };
  },
  methods: {
    sendParent() {
      console.log('sendParent');
    }
  }
};
</script>
