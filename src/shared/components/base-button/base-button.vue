<template>
  <button
    ref="buttonRef"
    :type="type"
    :class="{
      'mdc-button--raise': raised,
      'mdc-button--unelevated': unelevated,
      'mdc-button--outlined': outlined,
    }"
    class="mdc-button"
    @click="handleClick"
  >
    <div class="mdc-button__ripple"></div>
    <slot />
  </button>
</template>
<script lang="ts">
import {
  defineComponent,
  onMounted,
  onBeforeUnmount,
  ref,
  SetupContext,
} from 'vue';
import { MDCRipple } from '@material/ripple';

type Props = {
  type: string;
  raised: boolean;
  unelevated: boolean;
  outlined: boolean;
};

export default defineComponent({
  name: 'BaseButton',
  props: {
    type: {
      type: String,
      default: 'button',
    },
    raised: {
      type: Boolean,
      default: false,
    },
    unelevated: {
      type: Boolean,
      default: false,
    },
    outlined: {
      type: Boolean,
      default: false,
    },
  },
  setup(props: Props, context: SetupContext) {
    const buttonRef = ref<HTMLButtonElement>();
    let mdc: MDCRipple | null = null;

    const initializeMDC = () => {
      if (typeof buttonRef.value !== 'undefined') {
        mdc = MDCRipple.attachTo(buttonRef.value);
      }
    };
    onMounted(() => {
      initializeMDC();
    });

    const destoryMDC = (mdc: MDCRipple | null) => {
      if (mdc !== null) {
        mdc.destroy();
      }
    };
    onBeforeUnmount(() => {
      destoryMDC(mdc);
    });

    const handleClick = (event: Event) => {
      context.emit('click', event);
    };

    return {
      handleClick,
      props,
      buttonRef,
    };
  },
});
</script>
<style lang="sass" scoped>
@import "@material/button/mdc-button"
</style>
