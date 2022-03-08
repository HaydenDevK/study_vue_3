<template>
  <div>PropsString _ {{ PropsString }}</div>
  <div>PropsNumbers : {{ PropsNumbers }}</div>
  <div v-if="PropsNumbers != undefined">PropsNumbers : {{ PropsNumbers }}</div>
  <!--
      v-if="PropsNumbers != undefined" : 렌더링 O
      v-if="PropsNumbers" : 렌더링 X
      v-if="!!PropsNumbers" : 렌더링 X
  -->

  <div>
    PropsObject :
    {{ PropsObject.name }}, {{ PropsObject.gender }},
    {{ PropsObject.job }}
  </div>
  ---------------------
</template>

<script>
export default {
  name: 'ComponentChild',
  props: {
    PropsString: {
      type: String,
      defualt: 'props default string'
    },
    PropsNumbers: {
      type: Number,
      default: 0 // 부모에서 넘어온 값이 없어도, 디폴트 값을 정의해두면 그 값이 바인딩 된다.
    },
    PropsObject: {
      type: Object,
      /*
      default: {
          name: 'default-name',
          gender: 'default-gender',
          job: 'default-job',
      }
      위와 같이 작성해야할 것 같지만, 아니고 아래와 같이 함수 형태로 작성해야한다.
      */
      default: () => {
        return {
          name: '(default-name)',
          gender: '(default-gender)',
          job: '(default-job)'
        };
      }
    }
  }
  /* props
    1. 부모에게 받은 데이터
    2. 자식이 수정하면 안된다.
    3. 어떤 데이터를 받을 것인지 (datatype 등), 받은 데이터가 없을 때 디폴트 데이터 등을 정의할 수 있고, 가급적 자세히 명시해두는 것이 바람직하다.
  */
};
</script>
