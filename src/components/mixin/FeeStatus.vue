<template>
  <div>
    <div>합산 요금 : {{ totalMoney }}</div>
    <button @click="addMoney(50)">50</button>
    <button @click="addMoney(100)">100</button>
    <button @click="addMoney(150)">150</button>
    <button @click="addMoney(200)">200</button>
  </div>
</template>

<script>
import moneyMixin from '../../mixins/moneyMixins';
export default {
  name: 'FeeStatus',
  mixins: [moneyMixin],
  data() {
    return {};
  }
};
</script>
