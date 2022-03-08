<template>
  <div>RerenderChildKey</div>
</template>

<script>
export default {
  name: 'RerenderChildKey',
  mounted() {
    console.log(`RerenderChildKey is rendered!`);
  },
  unmounted() {
    console.log(`RerenderChildKey is unmounted!`);
  }
};
</script>
