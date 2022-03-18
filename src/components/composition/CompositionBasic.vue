<template>
  <h1>22. Composition</h1>
  <TestComponent />
  <TestComponent2 />
  <TestComponent3 />
  <CompositionLifeCycle />
</template>

<script>
import TestComponent from '@/components/composition/TestComponent';
import TestComponent2 from '@/components/composition/TestComponent2';
import TestComponent3 from '@/components/composition/TestComponent3';
import CompositionLifeCycle from '@/components/composition/CompositionLifeCycle';
export default {
  name: 'CompositionBasic',
  components: {
    TestComponent,
    TestComponent2,
    TestComponent3,
    CompositionLifeCycle
  }
};
</script>
