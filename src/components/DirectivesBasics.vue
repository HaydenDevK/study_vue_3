<template>
  <h1>9. Directives</h1>

  <h3>[ v-once ]</h3>
  <div>{{ number }}</div>
  <div v-once>{{ number }}</div>
  <!-- v-once : 바인딩 하는 태그에 붙이면 이 태그의 값은 변경이 안된다 -->
  <button @click="changeNumber">Change Number</button>

  <h3>[ v-pre ]</h3>
  <div v-pre>{{ number }}</div>
  <!-- v-pre : 컴파일에서 제외되기 때문에, 코드가 그대로 노출된다. -->

  <h3>[ 커스터마이징 디렉티브 ]</h3>
  v-focus
  <input type="text" v-focus />
  v-highlight
  <input type="text" v-highlight />
</template>

<script>
export default {
  name: 'DirectivesBasics',
  data() {
    return {
      number: 1
    };
  },
  directives: {
    // 로컬 커스텀 디렉티브
    focus: {
      mounted(ele) {
        // ele : 디렉티브가 선언된 element
        // element가 DOM에 삽입된 시점(mounted)에 (methods를 mounted 시점에 실행시키듯이)
        ele.focus();
        // 해당 input element에 focus
      }
    },
    highlight: {
      mounted(ele) {
        console.log(ele); // refs 선택자처럼 엘리먼트로 찍힌다. <input type="text">
        console.log({ ele }); // 객체로 찍힌다.
        ele.oninput = () => {
          // oninput : input의 on 이벤트 중 하나로 '뭔가가 작성이 되었을 때'
          // 해당 이벤트에 메서드를 연결해줘야 한다.
          ele.style.background = 'salmon';
          ele.style.color = '#FFF';
          /* Q
            동적인 UI를 여러 개 만들 때 활용할 수 있지 않을까?
            다양한 실무 예제를 알고싶다.
           */
        };
      }
    }
  },
  methods: {
    changeNumber() {
      console.log('number changed');
      this.number++;
    }
  }
};
</script>
