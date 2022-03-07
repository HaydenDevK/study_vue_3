<template>
  <h1>3. Class Binding :</h1>
  <!-- static -->
  <div class="text-right">static class</div>

  <!-- 정적 binding, static -->
  <div v-bind:class="textRight" class="text-red">정적 class binding</div>

  <!-- 동적 binding (조건문) -->
  <div :class="isDone === true ? 'text-red' : 'text-blue'">
    삼항연산자로 동적 class binding
  </div>

  <div
    :class="{
      'text-red': isDone === false,
      'border-red': username === 'user'
    }"
  >
    Object 형태의 동적 class binding
  </div>
  <!-- 여러 개의 클래스 바인딩 가능 (예외처리 X)
        { 클래스1 : 조건문1 },
        { 클래스2 : 조건문2 }
  -->

  <div
    :class="[
      isDone === true ? 'text-red' : 'text-blue',
      username === 'user' ? 'border-red' : 'border-blue'
    ]"
  >
    Array 형태의 동적 class binding
  </div>
  <!-- 여러 개의 클래스 바인딩 가능 (예외처리까지 O)
    [ 
        조건문1 ? 클래스1 : 클래스2,
        조건문2 ? 클래스3 : 클래스4
    ]
  -->
</template>

<script>
export default {
  name: 'BindingClass',
  data() {
    return {
      textRight: 'text-right',
      isDone: true,
      username: 'user'
    };
  }
};
</script>

<style scoped>
.text-right {
  text-align: right;
}
.text-red {
  color: red;
}
.text-blue {
  color: blue;
}
.border-red {
  border: 1px solid red;
}
.border-blue {
  border: 1px solid blue;
}
</style>
