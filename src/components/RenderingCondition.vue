<template>
  <h1>4. Conditional Rendering : v-once, v-if/v-else-if/v-else, template</h1>

  <h3>
    [ v-once : 데이터가 동적으로 변화해도, 해당 태그에 바인딩된 값은 처음
    렌더링된 후 변경되지 않게한다. ]
  </h3>
  <div v-text="user.name"></div>
  <div>{{ user.name }}</div>
  <!-- <div v-once>{{ user.name }}</div> 이렇게 작성도 가능 -->
  <div v-once v-text="user.name"></div>
  <input type="text" v-model="user.name" />

  <h3>[ v-if / v-else-if / v-else ]</h3>
  <h4>1 )</h4>
  <button @click="showName = !showName">
    {{ showName ? '숨기기' : '보이기' }}
  </button>
  <div v-if="showName">{{ user.name }}</div>
  <div v-else>이름은 가려져있습니다.</div>
  <h4>2 )</h4>
  <input type="number" v-model="user.age" />
  <div v-if="user.age >= 20">성인입니다.</div>
  <!-- v-if v-else-if v-else 사이에 다른 태그가 존재하면 안된다. -->
  <!-- <span></span> -->
  <div v-else-if="user.age >= 10 && user.age < 20">10대 입니다.</div>
  <div v-else-if="user.age < 0">정상적인 나이를 입력하세요.</div>
  <div v-else>어린이 입니다.</div>

  <h3>[ v-show ]</h3>
  <div v-if="showName">{{ user.name }} IF</div>
  <!-- 렌더링 or 비렌더링 (렌더링 자체가 안되기 때문에, 용량이 크고 새로운 데이터를 불러와야 할 때 적합) -->
  <div v-show="showName">{{ user.name }} SHOW</div>
  <!-- 렌더링은 일단 되고, display: none -->

  <ul>
    <template v-if="quastion === 'frontend'">
      <li>HTML</li>
      <li>CSS</li>
      <li>JS</li>
    </template>
    <template v-else>
      <li>Java</li>
      <li>Python</li>
      <li>C#</li>
    </template>
    <!-- 
        ul 태그 안에 div가 들어가면 안되고, 그저 그룹 처리 역할만을 위해 필요한 부모 태그이므로, 
        이런 경우 template으로 대체하면 된다.
        이 template 태그는 돔트리 상 존재하지 않는다.
    -->
  </ul>
</template>

<script>
export default {
  name: 'RenderingCondition',
  data() {
    return {
      user: {
        name: 'user',
        age: 20,
        job: 'programmer'
      },
      showName: true,
      quastion: 'frontend'
    };
  }
};
</script>
