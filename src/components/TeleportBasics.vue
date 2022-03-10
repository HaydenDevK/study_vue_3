<template>
  <h1>17. Teleport</h1>
  <h3>[ 기본 ]</h3>
  <div class="teleport-1">this is inside of app</div>
  <teleport to="#outside-app">
    <div class="teleport-1">this is outside of app (teleport 1)</div>
  </teleport>

  <h3>[ 심화 : disabled, ]</h3>
  <h5>- disabled</h5>
  <button @click="show = !show">Teleport Show</button>
  <teleport to="#outside-app" :disabled="teleportToggle">
    <!--
      조건 boolean인 teleportToggle true면 teleport되어 #outside-app에 렌더링되고,
      false면 #app에 렌더링된다.
    -->
    <div
      v-if="show"
      @click="teleportToggle = !teleportToggle"
      class="teleport-2"
    >
      (teleport 2)
      <button @click="teleportToggle = !teleportToggle">Teleport Toggle</button>
      <button @click="show = !show">hide</button>
    </div>
  </teleport>
  <!-- teleport
    1. index.html의 #app 밖에 엘리먼츠를 작업하고 싶을 때 사용
    2. to 속성에 인자로 정의한 선택자로 전송된다.
    3. :disabled="true" :disabled="false"로 teleport 사용 유무 조작 가능하다.
    4. :disabled="조건 boolean data의 이름"
    5. 
  -->
</template>

<script>
export default {
  name: 'TeleportBasics',
  data() {
    return {
      teleportToggle: false,
      show: false
    };
  }
};
</script>

<style scoped>
.teleport-1 {
  background: rgba(0, 0, 0, 0.5);
  color: #fff;
}
.teleport-2 {
  background: rgba(0, 0, 0, 0.5);
  color: #fff;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
