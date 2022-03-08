<template>
  <div>RerenderChildIf</div>
</template>

<script>
export default {
  name: 'RerenderChildIf',
  mounted() {
    console.log('RerenderChildIf is rendered!');
  },
  unmounted() {
    console.log('RerenderChildIf is unmounted!');
  }
};
</script>
