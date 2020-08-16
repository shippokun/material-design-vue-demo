<template>
  <header class="mdc-top-app-bar" ref="header">
    <div class="mdc-top-app-bar__row">
      <section
        class="mdc-top-app-bar__section mdc-top-app-bar__section--align-start"
      >
        <button
          class="material-icons mdc-top-app-bar__navigation-icon mdc-icon-button"
          aria-label="Open navigation menu"
        >
          menu
        </button>
        <span class="mdc-top-app-bar__title">Page title</span>
      </section>
      <section
        class="mdc-top-app-bar__section mdc-top-app-bar__section--align-end"
        role="toolbar"
      >
        <button
          class="material-icons mdc-top-app-bar__action-item mdc-icon-button"
          aria-label="Favorite"
        >
          favorite
        </button>
        <button
          class="material-icons mdc-top-app-bar__action-item mdc-icon-button"
          aria-label="Search"
        >
          search
        </button>
        <button
          class="material-icons mdc-top-app-bar__action-item mdc-icon-button"
          aria-label="Options"
        >
          more_vert
        </button>
      </section>
    </div>
  </header>
</template>
<script lang="ts">
import { defineComponent, ref, onMounted, onUnmounted } from 'vue';
import { MDCTopAppBar } from '@material/top-app-bar';

export default defineComponent({
  name: 'BaseTopAppBar',
  setup() {
    const header = ref<HTMLHeadElement>();
    let mdc: MDCTopAppBar | null = null;

    const initialMDC = () => {
      if (typeof header.value !== 'undefined') {
        mdc = MDCTopAppBar.attachTo(header.value);
      }
    };
    onMounted(() => {
      initialMDC();
    });

    const destroyMDC = () => {
      if (mdc !== null) {
        mdc.destroy();
      }
    };
    onUnmounted(() => {
      destroyMDC();
    });

    return {
      header,
    };
  },
});
</script>
<style lang="sass" scoped>
@import '@material/top-app-bar/mdc-top-app-bar'
@import '@material/icon-button/mdc-icon-button'

.mdc-top-app-bar
  position: static
</style>
