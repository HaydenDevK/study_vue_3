<template>
  <div>
    <div>저축 총액 : {{ totalMoney }}</div>
    <button @click="addMoney(1000)">1000</button>
    <button @click="addMoney(2000)">2000</button>
    <button @click="addMoney(1500)">1500</button>
    <button @click="addMoney(2200)">2200</button>
  </div>
</template>

<script>
import moneyMixin from '../../mixins/moneyMixins';
export default {
  name: 'SavingStatus',
  mixins: [moneyMixin],
  data() {
    return {};
  }
};
</script>
