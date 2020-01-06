<template>
  <header class="AppHeader">
    <div class="container">
      <h1 class="AppHeader__title">{{ title }}</h1>
      <h2 class="AppHeader__subtitle" v-if="subtitle">{{ subtitle }}</h2>
    </div>
  </header>
</template>

<script>
export default {
  name: 'AppHeader',

  props: {
    title: {
      type: String,
      required: true
    },
    subtitle: {
      type: String,
      default: null
    }
  }
};
</script>

<style lang="scss">
.AppHeader {
  background: darken(#2c3e50, 10%);
  padding: 2rem 1rem;
  color: #fff;

  &__title {
    margin: 0;
    font-size: 3.2rem;
  }

  &__subtitle {
    margin: 0;
    color: lighten(#2c3e50, 40%);
    font-size: 1.8rem;
  }
}
</style>
