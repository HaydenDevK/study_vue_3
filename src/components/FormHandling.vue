<template>
  <h1>8. Form Handling</h1>
  {{ user }}
  <form>
    <div>
      <h3>[ input text ]</h3>
      <label for="name">이름</label>
      <!-- 
        label 태그 :
          클릭 시 연결된 input 태그가 활성화
        for 속성 : 
          label 태그의 기본 속성
          input 태그의 id를 가리킨다.
      -->
      <input type="text" id="name" v-model="user.name" />
      {{ user.name }}
      <!--
        한글 입력 시 실시간 연동안되는 이유 : 
        Vue에서는, IME(조합형 문자)가 필요한 언어의 경우 IME(조합)중에는 v-model이 업데이트 되지않는 문제가 있기 때문이다.
        이 경우, 
        1. <input :value="user.name" @input="user.name = $event.target.value"/>
        2. @input="setValue($event)" setValue(e){this.user.name = $event.target.value} // 똑같은 내용인데 함수로 만든 것이다.
      -->
    </div>
    <div>
      <h3>[ input number ]</h3>
      <label for="age">나이</label>
      <input type="number" id="age" v-model="user.age" />
    </div>
    <div>
      <h3>[ select ]</h3>
      <label for="city">사는 곳</label>
      <select id="city" v-model="user.city">
        <!--
          1. user.city가 없지만, 여기서 입력한대로 user에 city가 추가된다.
            즉, data에 초기 값을 선언해두지 않아도 된다. 하지만 가급적 선언하는 게 맞다.
          2. select 태그의 v-model 속성이 option 태그 중에 선택한 태그의 value와 연동된다.
        -->
        <option value="seoul">서울</option>
        <option value="daejeon">대전</option>
        <option value="daegu">대구</option>
        <option value="busan">부산</option>
        <option value="gwangju">광주</option>
      </select>
    </div>
    <div>
      <h3>[ multiple select ]</h3>
      <label for="favorite-food">좋아하는 음식</label>
      <select id="favorite-food" v-model="user.favorite" multiple>
        <!-- 
          multiple select
          windows: CTRL, SHIFT
          mac: COMMAND
        -->
        <option
          v-for="option in foodOptions"
          :key="option.code"
          :value="option.code"
        >
          {{ option.label }}
        </option>
      </select>
    </div>
    <div>
      <h3>[ input checkbox ]</h3>
      <label for="job">직업</label>
      <!-- Q. 연결할 input id가 없는데 for가 필요한가? -->
      프로그래머<input type="checkbox" value="programmer" v-model="user.job" />
      유튜버<input type="checkbox" value="youtuber" v-model="user.job" />
      댄서<input type="checkbox" value="dancer" v-model="user.job" />
      <!--
        with clickable label
        1. <label><input type="checkbox"value="programmer" v-model="user.job">프로그래머</label>
        2. <input type="checkbox" name="checkbox" id="checkbox_id" value="value">
            <label for="checkbox_id">Text</label>
      -->
    </div>
    <div>
      <h3>[ input radio ]</h3>
      <label for="gender">성별</label>
      <!-- Q. 연결할 input id가 없는데 for가 필요한가? -->
      남<input type="radio" value="male" v-model="user.gender" /> 여<input
        type="radio"
        value="male"
        v-model="user.gender"
      />
    </div>
  </form>
  <!--
    action :
    form 태그의 기본 속성
    form을 전송할 때 추가 액션
  -->
</template>

<script>
export default {
  name: 'FormHandling',
  data() {
    return {
      foodOptions: [
        {
          label: '짜장면',
          code: 'CJ'
        },
        {
          label: '짬뽕',
          code: 'CP'
        },
        {
          label: '탕수육',
          code: 'TS'
        }
      ],
      user: {
        name: '',
        age: 0,
        city: 'seoul',
        favorite: [], // 배열로 초기화 해두지 않으면, multiple한 값이 들어가지 않는다.
        job: []
      }
    };
  },
  methods: {}
};
</script>
<style scoped>
label {
  font-size: 16px;
  font-weight: bold;
  margin-right: 1rem;
}
div {
  margin-bottom: 1rem;
}
</style>
