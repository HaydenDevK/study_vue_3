<template>
  <div>Menu 3</div>
  <input type="text" v-model="userName" />
  <!-- 컴포넌트가 렌더링된 후 입력한 값이 리렌더링 시에도 유지되게 => keep alive -->
</template>

<script>
export default {
  name: 'ChildComp3',
  data() {
    return {
      userName: ''
    };
  }
};
</script>
