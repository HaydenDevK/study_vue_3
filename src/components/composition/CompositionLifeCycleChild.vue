<template>
  <div>{{ fullName }}</div>
  <button @click="sendParent">Child Click</button>
</template>

<script>
import { computed } from 'vue';
export default {
  name: 'CompositionLifeCycleChild',
  props: ['firstName', 'lastName'],
  emits: ['sendParent'], // Q. 예제에서는 생략되어있었는데, 생략 시 경고 : Extraneous non-emits event listeners (sendParent) were passed to component but could not be automatically inherited because component renders fragment or text root nodes. If the listener is intended to be a component custom event listener only, declare it using the "emits" option.
  setup(props, context) {
    const fullName = computed(() => {
      return `${props.firstName} ${props.lastName}`;
      // props를 이렇게 받는다고..?생소하다
      // setup에서 this에 접근할 수 없다.
    });

    // emit
    console.log(context);
    const sendParent = function () {
      context.emit('sendParent');
    };

    return {
      fullName,
      sendParent
    };
  }
};
</script>
