<template>
  <div v-if="option" class="SelectedOption">
    {{ option }}
  </div>
</template>

<script>
export default {
  name: 'AppSelectedOption',

  props: {
    option: {
      type: String,
      default: null
    }
  }
};
</script>

<style lang="scss">
.SelectedOption {
  padding: 3.2rem;
  margin-bottom: 2.2rem;
  background: #fff;
  text-align: center;
  font-size: 2.4rem;
  font-weight: bold;
  color: #e91e63;
  border-radius: 2px;
  box-shadow: 0 2.4rem 1.2rem -1.2rem rgba(darken(#2c3e50, 15%), 0.4);
}
</style>
