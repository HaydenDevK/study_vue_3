<template>
  <h3>[ ]</h3>
  <h4>CompLevel3</h4>
  <div>inject userNameProvide : {{ userNameProvide }}</div>
</template>

<script>
export default {
  name: 'CompLevel3',
  data() {
    return {};
  },
  inject: ['userNameProvide']
};
</script>
