<template>
  <base-button @click="clickEvent" outlined>
    <template v-slot:default>
      <span class="mdc-button__label">Text Button</span>
    </template>
  </base-button>
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
