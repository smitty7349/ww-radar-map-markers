<template>
  <div class="card flex justify-center">
      <InputText type="text" v-model="value":style="textStyle" />
  </div>
</template>

<script>
import InputText from 'primevue/inputtext';
import PrimeVue from 'primevue/config';
import Aura from '@primevue/themes/aura';
import "primevue/resources/themes/aura/theme.css"; // Import the theme CSS

export default {
  beforeCreate() {
    // Use PrimeVue with the specified configuration including ripple and input variant
    this.$.appContext.app.use(PrimeVue, {
      ripple: true,
      inputVariant: 'filled',
      theme: {
        preset: Aura,
        options: {
          prefix: 'p',
          darkModeSelector: 'system',
          cssLayer: false
        }
      }
    });
    this.$.appContext.app.component('input-text', InputText);
  },
  props: {
    content: { type: Object, required: true },
  },
  computed: {
    textStyle() {
      return {
        color: this.content.textColor,
      };
    },
  },
  data() {
        return {
            value: null
        }
      },
};
</script>

<style lang="scss" scoped>
.my-element {
  p {
    font-size: 18px;
  }
}
</style>
