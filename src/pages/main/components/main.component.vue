<template>
  <base-button
    :type="button"
    :raised="false"
    :unelevated="false"
    :outlined="false"
    @click="clickEvent"
  />
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
