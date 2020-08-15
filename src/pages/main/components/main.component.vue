<template>
  <base-button @click="clickEvent" />
</template>
<script lang="ts">
import { defineComponent } from 'vue';

import { BaseButton } from '@/shared';

export default defineComponent({
  name: 'MainComponent',
  components: {
    BaseButton,
  },
  setup() {
    const clickEvent = (event: Event) => {
      console.log(event);
    };
    return {
      clickEvent,
    };
  },
});
</script>
