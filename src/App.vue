<template>
  <BindingText />
  <BindingAttr />
  <BindingClass />
  <RenderingCondition />
  <RenderingList />
  <RenderingConditionalList />
  <StudyMethods />
</template>

<script>
import BindingText from './components/BindingText';
import BindingAttr from './components/BindingAttr';
import BindingClass from './components/BindingClass';
import RenderingCondition from './components/RenderingCondition';
import RenderingList from './components/RenderingList';
import RenderingConditionalList from './components/RenderingConditionalList';
import StudyMethods from './components/StudyMethods';

export default {
  name: 'App',
  components: {
    BindingText,
    BindingAttr,
    BindingClass,
    RenderingCondition,
    RenderingList,
    RenderingConditionalList,
    StudyMethods
  }
};
</script>
