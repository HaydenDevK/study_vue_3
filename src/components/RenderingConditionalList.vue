<template>
  <h1>
    6. Conditional List Rendering : 데이터 가공(filter, map, reduce), 조건문
  </h1>

  <h3>[ 원본 ]</h3>
  <ul>
    <li v-for="(city, cityIndex) in cities" :key="cityIndex">
      {{ city.name }}
    </li>
  </ul>

  <h3>[ 데이터 가공 (filter로 조건문에 해당하는 요소만) ]</h3>
  <ul>
    <li
      v-for="(city, cityIndex) in cities.filter((c) => c.province === '경상도')"
      :key="cityIndex"
    >
      {{ city.name }}
    </li>
  </ul>

  <h3>[ 조건문은 (template 가라 태그 활용) ]</h3>
  <ul>
    <template v-for="(city, cityIndex) in cities" :key="cityIndex">
      <li v-if="city.province === '경상도'">
        {{ city.name }}
      </li>
    </template>
  </ul>

  <h3>[ 조건문 _ 실패1 ]</h3>
  <ul>
    <li v-for="(city, cityIndex) in cities" :key="cityIndex">
      {{ city.name }}
    </li>
  </ul>
  <!-- 
    1. li 태그에 넣기엔 v-for랑 겹쳐서 불가하다.
    2. ul 태그에 넣기엔 v-if="city.province === '경상도'" => Property "city" was accessed during render but is not defined on instance 에러로 불가하다.
  -->

  <h3>[ 조건문 _ 실패2 ]</h3>
  <ul>
    <li v-for="(city, cityIndex) in cities" :key="cityIndex">
      <span v-if="city.province === '경상도'">{{ city.name }}</span>
    </li>
    <!-- 
        텍스트 노드는 조건문에 합당한 2개만 생성 되었지만,
        li 태그 자체는 전체 6개가 생성되는 문제가 있다. 
    -->
  </ul>
</template>

<script>
export default {
  name: 'RenderingConditionalList',
  data() {
    return {
      cities: [
        {
          name: '서울',
          province: '경기도'
        },
        {
          name: '대전',
          province: '충청도'
        },
        {
          name: '대구',
          province: '경상도'
        },
        {
          name: '부산',
          province: '경상도'
        },
        {
          name: '인천',
          province: '경기도'
        },
        {
          name: '광주',
          province: '전라도'
        }
      ]
    };
  }
};
</script>
