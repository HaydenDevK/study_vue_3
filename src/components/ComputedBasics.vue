<template>
  <h1>10. Computed</h1>
  <div>1. {{ grade.math + grade.kor + grade.eng + grade.sci }}</div>
  <div>2. totalScore : {{ totalScore }}</div>
  <div>3. getTotalScore : {{ getTotalScore() }}</div>
  <!-- computed vs methods
    computed : 값이 캐싱된다. 해당 값이 변화해야 재연산이 실행된다. 비교적 간단한 연산 용
    methods : 작성한 값 외에 그 어떤 값이 변해도, 재연산이 실행된다.
  -->
  <input type="number" v-model="grade.math" />
  <input type="text" v-model="studentName" />
  <!--
    grade가 변경되면 => totalScore(computed), getTotalScore(methods) 둘 다 실행
    studentName가 변경되면 => getTotalScore(methods)만 실행
  -->
</template>

<script>
export default {
  name: 'ComputedBasics',
  data() {
    return {
      address1: '서울시',
      address2: '마포구',
      address3: '월드컵북로',
      grade: {
        math: 70,
        kor: 90,
        eng: 90,
        sci: 55
      },
      studentName: ''
    };
  },
  computed: {
    address() {
      return `${this.address1} - ${this.address2} - ${this.address3}`;
    },
    totalScore() {
      console.log('totalScore(computed)');
      // return grade.math + grade.kor + grade.eng + grade.sci;
      // 비구조화 destructuring 디스트럭쳐링
      const { math, kor, eng, sci } = this.grade;
      return math + kor + eng + sci;
    }
  },
  methods: {
    getTotalScore() {
      console.log('getTotalScore(methods)');
      const { math, kor, eng, sci } = this.grade;
      return math + kor + eng + sci;
    }
  }
};
</script>
