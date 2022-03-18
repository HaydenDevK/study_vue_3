<template>
  <div>child component</div>
  <input type="text" v-model="childString" /><br />
</template>

<script>
export default {
  name: 'RefsChildComp',
  data() {
    return {
      childString: 'childString'
    };
  },
  methods: {
    sayHello() {
      console.log('say hello');
    }
  }
};
</script>
