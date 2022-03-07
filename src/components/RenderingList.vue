<template>
  <h1>5. List Rendering : v-for</h1>

  <h3>[ for in, for of ]</h3>
  <ul>
    <li v-for="(fruit, index) in fruits" :key="index">
      {{ fruit }} {{ index }}
    </li>

    <li v-for="(fruit, index) of fruits" :key="index">
      {{ fruit }} {{ index }}
    </li>
    <!-- fruit는 임의로 지정한 이름. item, prop 등 다른 이름으로 해도 상관없다. -->
    <!-- 보간법에는 간략한 수식 1개까지 작성할 수 있다. -->
    <!-- for in, for of 둘 다 된다. -->
  </ul>

  <h3>[ index, value, key 모두 사용 ]</h3>
  <ul>
    <li v-for="(value, key, index) in user" :key="index">
      {{ index }}.{{ key }} : {{ value }}
    </li>
  </ul>

  <h3>[ 숫자로 반복문 ]</h3>
  <ul>
    <li v-for="n in 10" :key="n">{{ n }}</li>
  </ul>

  <h3>[ 중첩 반복문 ]</h3>
  <div v-for="(animal, animalIndex) in animals" :key="animalIndex">
    <div>animal : {{ animal.name }}</div>
    <div>
      food :
      <ul>
        <li
          v-for="(favorite, favoriteIndex) in animal.favorites"
          :key="favoriteIndex"
        >
          {{ favorite }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RenderingList',
  data() {
    return {
      fruits: ['banana', 'strawberry', 'apple', 'melon'],
      user: {
        name: 'kim',
        age: 30,
        joo: 'programmer'
      },
      animals: [
        {
          name: 'monkey',
          size: 'medium',
          favorites: ['banana', 'apple']
        },
        {
          name: 'lion',
          size: 'big',
          favorites: ['deer', 'cow']
        },
        {
          name: 'rat',
          size: 'small',
          favorites: ['cheese', 'rice']
        }
      ]
    };
  }
};
</script>
