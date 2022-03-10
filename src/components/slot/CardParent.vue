<template>
  <h1>16. Slot</h1>
  <h3>[ 기본 ]</h3>
  <!-- 1. 부모가 자식의 slot에 아무것도 안 보내면 : 자식이 지정해놓은 default -->
  <CardSlot> </CardSlot>

  <!-- 2. 부모가 자식에게 slot에 string 보내기 -->
  <CardSlot> send string for slot </CardSlot>

  <!-- 3. 부모가 자식에게 slot에 image 보내기 -->
  <CardSlot>
    <img src="https://placeimg.com/100/50/any" alt="random" />
  </CardSlot>

  <!-- 4. 부모가 자식에게 slot에 list 보내기 -->
  <CardSlot>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
    </ul>
  </CardSlot>

  <h3>[ 여러 개의 slot ]</h3>
  <!-- 5. 부모가 자식에게 slot에 list 보내기 -->
  <CardSlot>
    <template v-slot:header>
      <!-- 
          자식의 slot의 name=""와 동일하게
          부모의 template 태그에 v-slot:""
      -->
      <div>send header</div>
    </template>
    <template v-slot:body>
      <div>send body</div>
    </template>
    <template v-slot:footer>
      <div>send footer</div>
    </template>
    <template v-slot:default>
      <div>send default</div>
    </template>
  </CardSlot>
</template>

<script>
import CardSlot from '@/components/slot/CardSlot';
export default {
  name: 'CardParent',
  components: {
    CardSlot
  }
};
</script>
