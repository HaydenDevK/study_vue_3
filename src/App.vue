<template>
  <BindingText />
  <BindingAttr />
  <BindingClass />
</template>

<script>
import BindingText from './components/BindingText';
import BindingAttr from './components/BindingAttr';
import BindingClass from './components/BindingClass';

export default {
  name: 'App',
  components: {
    BindingText,
    BindingAttr,
    BindingClass
  }
};
</script>

<style scoped></style>
