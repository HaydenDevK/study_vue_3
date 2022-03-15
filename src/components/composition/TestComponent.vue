<template>
  <h3>[ 반응성 주입 방법 1. ref ]</h3>
  <h4>
    - 반응성을 잃는다? : 복사한 변수에 원본 값의 변경 사항이 반영이 안된다.
    (이게 자바스크립트 원래 특성이고, 여기에 반응성을 주입시켜야 한다.)
    <br />
  </h4>
  <div>origin : {{ origin }}</div>
  <div>copy : {{ copy }}</div>

  <h4>- ref로 반응형 주입 (모든 자료형 가능)</h4>
  <div>originRef : {{ originRef }}</div>
  <div>copyRef : {{ copyRef }}</div>

  <h3>
    [ 반응성 주입 방법 2. reactive (Array, Object, Map, Set에 반응성 주입) ]
  </h3>
  <div>state.userName : {{ state.userName }}</div>
  <div>stateCopy.userName : {{ stateCopy.userName }}</div>
  <h4>- reactive로 반응형 주입</h4>
  <div>stateReactive.userName : {{ stateReactive.userName }}</div>
  <div>stateReactiveCopy.userName : {{ stateReactiveCopy.userName }}</div>

  <h3>[ 반응형 유틸리티 1. toRefs (`state.` 생략) ]</h3>
  <div>userName2 : {{ userName2 }}</div>
</template>

<script>
import { reactive, toRefs, ref } from 'vue';
export default {
  name: 'TestComponent',
  setup() {
    // 반응성을 잃는다? ref?
    let origin = true;
    let copy = origin; // 1. 원본을 다른 변수에 대입한 후에
    origin = false; // 2. 원본 값이 변경되면, 반영이 안된다.
    let originRef = ref(true); // 3. 이 때 이렇게 반응성을 주입하고 싶은 원본 값을 ref로 감싼다.
    let copyRef = originRef;
    originRef.value = false; // 4. 반응성이 주입되어, 원본 값의 변경 사항이 반영된다. (주의! .value 로 값에 접근할 수 있다. 이유는 originRef 찍어보면 객체가 나온다.)

    // reactive
    const state = {
      userName: 'Sophie'
    }; // 객체를 인수로 갖고 reactive 함수를 돌린 결과값
    let stateCopy = state;
    state.userName = 'SophieChanged';

    const stateReactive = reactive({
      userName: 'Sophie'
    });
    let stateReactiveCopy = stateReactive;
    stateReactive.userName = 'SophieChanged';

    const state2 = reactive({
      userName2: 'Sophie2'
    });

    return {
      origin, // origin = origin
      originRef,
      copy,
      copyRef,
      state,
      stateCopy,
      stateReactive,
      stateReactiveCopy,
      ...toRefs(state2)
      /* toRefs
        userName2: state.userName 원래 이렇게 보내야 template 영역에서 state.을 생략하고 userName으로 호출할 수 있는데
        이렇게 내부 프로퍼티를 직접 연결하면 (값 변경 시 출처 쪽에도 반영되는) **반응성** 이라는 것을 잃는다.
        그래서 state의 반응성을 유지시켜주기 위해 toRefs 메서드로 가공을 거쳐야한다! 고 생각하면 쉬운 것 같다.
        Q. spread operator가 필요한 이유 : 객체라서..?
      */
    };
  }
};
</script>
