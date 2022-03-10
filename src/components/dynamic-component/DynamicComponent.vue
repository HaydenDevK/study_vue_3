<template>
  <h1>15. Component Basics 4 : Dynamic Component (with Tab example)</h1>

  <button @click="active = 'ChildComp1'">Menu1</button>
  <button @click="active = 'ChildComp2'">Menu2</button>
  <button @click="active = 'ChildComp3'">Menu3</button>

  <h3>[ Dynamic Component X ]</h3>
  <ChildComp1 v-if="active === 'ChildComp1'" />
  <ChildComp2 v-if="active === 'ChildComp2'" />
  <ChildComp3 v-if="active === 'ChildComp3'" />

  <h3>[ Dynamic Component X (keep alive) ]</h3>
  <ChildComp1 v-if="active === 'ChildComp1'" />
  <ChildComp2 v-if="active === 'ChildComp2'" />
  <keep-alive>
    <ChildComp3 v-if="active === 'ChildComp3'" />
  </keep-alive>

  <h3>[ Dynamic Component O ]</h3>
  <component :is="active"></component>
  <!-- is 속성에 컴포넌트명(이 들어가는 데이터) -->

  <h3>[ Dynamic Component O (keep alive) ]</h3>
  <keep-alive>
    <component :is="active"></component>
  </keep-alive>
  <!-- keep alive
   keep alive 태그로 감싼 컴포넌트의 데이터가 항상 유지된다.
   keep alive 태그 안에는 컴포넌트 태그 1개만 들어갈 수 있다.
   당연한 얘기같지만, 새로고침 시에는 데이터가 삭제된다.
   어떻게 데이터가 유지될까? : 비활성 컴포넌트 인스턴스를 삭제하지 않고 캐시해두었다가, 캐시되는 방법이다. 자세한 로직은 모르겠지만, DOM 트리에서는 사라진다.
  -->
</template>

<script>
import ChildComp1 from '@/components/dynamic-component/ChildComp1';
import ChildComp2 from '@/components/dynamic-component/ChildComp2';
import ChildComp3 from '@/components/dynamic-component/ChildComp3';
export default {
  name: 'DynamicComponent',
  components: {
    ChildComp1,
    ChildComp2,
    ChildComp3
  },
  data() {
    return {
      active: 'ChildComp1'
    };
  }
};
</script>
