<template>
  <BindingText />
  <BindingAttr />
  <BindingClass />
  <BindingCondition />
</template>

<script>
import BindingText from './components/BindingText';
import BindingAttr from './components/BindingAttr';
import BindingClass from './components/BindingClass';
import BindingCondition from './components/BindingCondition';

export default {
  name: 'App',
  components: {
    BindingText,
    BindingAttr,
    BindingClass,
    BindingCondition
  }
};
</script>

<style scoped></style>
