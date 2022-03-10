<template>
  <h3>[ ]</h3>
  <h4>CompLevel2</h4>
  <CompLevel3 />
</template>

<script>
import CompLevel3 from '@/components/provide-inject/CompLevel3';

export default {
  name: 'CompLevel2',
  components: {
    CompLevel3
  },
  data() {
    return {};
  },
  methods: {}
};
</script>
