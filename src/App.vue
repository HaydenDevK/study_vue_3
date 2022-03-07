<template>
  <BindingText />
  <BindingAttr />
  <BindingClass />
  <RenderingCondition />
</template>

<script>
import BindingText from './components/BindingText';
import BindingAttr from './components/BindingAttr';
import BindingClass from './components/BindingClass';
import RenderingCondition from './components/RenderingCondition';

export default {
  name: 'App',
  components: {
    BindingText,
    BindingAttr,
    BindingClass,
    RenderingCondition
  }
};
</script>

<style scoped></style>
