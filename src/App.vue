<template>
  <BindingText />
  <BindingAttr />
  <BindingClass />
  <RenderingCondition />
  <RenderingList />
  <RenderingConditionalList />
  <MethodsFirst />
</template>

<script>
import BindingText from './components/BindingText';
import BindingAttr from './components/BindingAttr';
import BindingClass from './components/BindingClass';
import RenderingCondition from './components/RenderingCondition';
import RenderingList from './components/RenderingList';
import RenderingConditionalList from './components/RenderingConditionalList';
import MethodsFirst from './components/MethodsFirst';

export default {
  name: 'App',
  components: {
    BindingText,
    BindingAttr,
    BindingClass,
    RenderingCondition,
    RenderingList,
    RenderingConditionalList,
    MethodsFirst
  }
};
</script>
