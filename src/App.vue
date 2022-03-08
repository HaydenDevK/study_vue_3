<template>
  <div style="text-align: center; font-size: 40px; font-weight: bold">
    [ BASICS ]
  </div>
  <BindingText />
  <BindingAttr />
  <BindingClass />
  <RenderingCondition />
  <RenderingList />
  <RenderingConditionalList />
  <MethodsBasics />
  <EventsBasics />
  <FormHandling />
  <DirectivesBasics />
  <ComputedBasics />
  <WatchBasics />
  <ComponentParent />
  <hr />

  <div style="text-align: center; font-size: 40px; font-weight: bold">
    [ ADVENCED ]
  </div>
  <ComponentForceRerender />
</template>

<script>
import BindingText from './components/BindingText';
import BindingAttr from './components/BindingAttr';
import BindingClass from './components/BindingClass';
import RenderingCondition from './components/RenderingCondition';
import RenderingList from './components/RenderingList';
import RenderingConditionalList from './components/RenderingConditionalList';
import MethodsBasics from './components/MethodsBasics';
import EventsBasics from './components/EventsBasics';
import FormHandling from './components/FormHandling';
import DirectivesBasics from './components/DirectivesBasics';
import ComputedBasics from './components/ComputedBasics';
import WatchBasics from './components/WatchBasics';
import ComponentForceRerender from './components/advanced/force-rerender/RerenderParent';
import ComponentParent from './components/component-basic/ComponentParent';

export default {
  name: 'App',
  components: {
    BindingText,
    BindingAttr,
    BindingClass,
    RenderingCondition,
    RenderingList,
    RenderingConditionalList,
    MethodsBasics,
    EventsBasics,
    FormHandling,
    DirectivesBasics,
    ComputedBasics,
    WatchBasics,
    ComponentForceRerender,
    ComponentParent
  }
};
</script>

<style>
* {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
</style>
