<template>
  <BindingText />
  <BindingAttr />
  <BindingClass />
  <RenderingCondition />
  <RenderingList />
  <RenderingConditionalList />
</template>

<script>
import BindingText from './components/BindingText';
import BindingAttr from './components/BindingAttr';
import BindingClass from './components/BindingClass';
import RenderingCondition from './components/RenderingCondition';
import RenderingList from './components/RenderingList';
import RenderingConditionalList from './components/RenderingConditionalList';

export default {
  name: 'App',
  components: {
    BindingText,
    BindingAttr,
    BindingClass,
    RenderingCondition,
    RenderingList,
    RenderingConditionalList
  }
};
</script>
