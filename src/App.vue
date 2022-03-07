<template>
  <BindingText />
  <BindingStyle />
</template>

<script>
import BindingText from './components/BindingText';
import BindingStyle from './components/BindingStyle';

export default {
  name: 'App',
  components: {
    BindingText,
    BindingStyle
  }
};
</script>

<style scoped></style>
