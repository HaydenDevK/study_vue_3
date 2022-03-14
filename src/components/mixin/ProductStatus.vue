<template>
  <div>
    <div>전체 금액: {{ totalMoney }}</div>
    <button @click="addMoney(100)">100</button>
    <button @click="addMoney(200)">200</button>
    <button @click="addMoney(300)">300</button>
    <button @click="addMoney(400)">400</button>
  </div>
</template>

<script>
import moneyMixin from '../../mixins/moneyMixins';

export default {
  name: 'ProductStatus',
  mixins: [moneyMixin],
  data() {
    return {
      totalMoney: 9999 // mixin에 같은 이름의 data나 가 있을 경우, 컴포넌트의 data를 우선 시 한다.
    };
  }
};
</script>
