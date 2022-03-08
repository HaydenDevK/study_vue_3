<template>
  <h1>7. Events</h1>

  <h3>[ 기본 ]</h3>
  <div>
    {{ name }}
  </div>
  <button v-on:click="changeName">Change Name</button>
  <button
    v-on:mouseover="name = 'changed name'"
    v-on:mouseleave="name = 'origin name'"
  >
    Change Name
  </button>
  <br />
  <a v-on:click="movePage" href="#">이동</a>
  <!-- movePage(event) 이 매개변수 작성을 생략해도 Vue에서는 디폴트로 이벤트 객체를 인자로 넘긴다. -->
  <br />
  <a v-on:click.prevent="movePage" href="#">이동</a>
  <!-- prevent 작성 방법 2 -->
  <div>{{ number }}</div>
  <button v-on:click="increment(1)">+</button>
  <button v-on:click="decrement($event, 1)">-</button>
  <!-- 매개변수가 있는 경우에 이벤트 객체로 넘기고 싶다면, $ -->

  <h3>[ modifier ]</h3>
  <button v-on:click.right="changeName">Change Name (Right Click)</button>
  <!-- .right : 디폴트인 좌클릭이 아니라 우클릭에 클릭이벤트 발생 -->

  <h3>[ modifier2 ]</h3>
  <div>{{ number }}</div>
  <button v-on:click="increment(1)">+</button>
  <button v-on:click="decrement($event, 1)">-</button>
</template>

<script>
export default {
  name: 'EventsBasics',
  data() {
    return {
      name: 'origin name',
      number: 0
    };
  },
  methods: {
    changeName() {
      this.name = 'changed name';
    },
    movePage(event) {
      console.log(event); // Q.Vue에서는 디폴트로 이벤트 객체를 인자로 받는다? 내가 알기론 그렇지 못해서 안전하게 $event로 매개변수로 이벤트 객체를 넘겨주고, 함수에서 인수로 받아 쓰는 것으로 알고 있는데..
      event.preventDefault(); /* a 태그 디폴트 이벤트인 페이지 이동을 무효화
      <a v-on:click.prevent="movePage" href="https://www.naver.com">naver로 이동</a> 이렇게 작성하는 것과 동일 */
      const check = confirm('페이지를 이동하시겠습니까?'); // confirm : JS 내장 메서드. 이동 여부 확인
      check ? console.log('page 이동 O') : console.log('page 이동 X');
      // todo console.log를 실제 페이지 이동 코드로 대체
    },
    increment(num) {
      this.number += num;
    },
    decrement(event, num) {
      console.log(event); // $event
      this.number -= num;
    }
  }
};
</script>
