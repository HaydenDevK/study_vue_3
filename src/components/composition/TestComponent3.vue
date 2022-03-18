<template>
  <h3>[ computed ]</h3>
  <div>{{ userName }}</div>
  <h4>- number</h4>
  <div>
    price :
    <input type="number" v-model="price" />
    amount :
    <input type="number" v-model="amount" />
    total price :
    <input type="number" v-model="totalPrice" disabled />
  </div>

  <h4>- text</h4>
  <div>
    first :
    <input type="text" v-model="first" />
    last :
    <input type="text" v-model="last" />
    full name :
    <input type="text" v-model="fullNameComputed" disabled />
  </div>

  <h3>[ watch ]</h3>
  <input type="text" v-model="fullNameWatch" disabled />
  detail.job :
  <input type="text" v-model="detail.job" />

  <h4></h4>
</template>

<script>
import { ref, computed, reactive, toRefs, watch } from 'vue';
export default {
  name: 'TestComponent3',
  setup() {
    const userName = ref('Sophie');
    const price = ref(5000);
    const amount = ref(1);

    const totalPrice = computed(() => {
      return price.value + amount.value;
    });

    const state = reactive({
      first: 'Sophie',
      last: 'Kim',
      detail: {
        job: 'programmer'
      }
    });
    const fullNameComputed = computed(() => {
      return `${state.first} ${state.last}`;
    });

    // watch
    const fullNameWatch = '';
    // 이렇게 작성하면 안된다.
    // watch(state, (newValue, oldValue) => {
    //   console.log(newValue.first, oldValue.first);
    //   // newValue.first, oldValue.first가 동일하다.
    //   // Q. 위 현상의 이유가 state를 reactive로 선언해서라는데 정확히 왜인지 모르겠다.
    //   // Q. deep: true 설정을 안했는데, state 내부의 변경을 어떻게 감지하는거지? toRefs 때문인가 했는데 아니네.
    // });

    // 이렇게 작성해야한다.
    watch(
      () => state.first,
      (newValue, oldValue) => {
        // state.first의 변화가 감지되었을 때
        console.log(newValue, oldValue);
      }
    );
    watch(
      () => state.last,
      (newValue, oldValue) => {
        // state.last의 변화가 감지되었을 때
        console.log(newValue, oldValue);
      }
    );

    // deep만
    // watch(
    //   () => state.detail,
    //   (newValue, oldValue) => {
    //     console.log(newValue, oldValue);
    //     // state.detail이 변화하지 않아도 작동하네?
    //   },
    //   { deep: true } // state 객체 안의 detail 객체를 감시하려면 deep 설정
    // );

    // deep(객체 내부 객체까지 변화 감지) + newValue와 oldValue 다르게
    watch(
      () => {
        return { ...state.detail }; // newValue와 oldValue 다르게
      },
      (newValue, oldValue) => {
        console.log(newValue, oldValue);
      },
      { deep: true } // state 객체 안의 detail 객체를 감시하려면 deep 설정
    );
    return {
      userName,
      price,
      amount,
      totalPrice,
      ...toRefs(state),
      fullNameComputed,
      fullNameWatch
    };
  }
};
</script>
