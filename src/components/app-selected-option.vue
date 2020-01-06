<template>
  <div v-if="option" class="SelectedOption">
    <button class="SelectedOption__clear" @click="onClearOption">X</button>
    <div class="SelectedOption__label">
      {{ option }}
    </div>
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
  },

  methods: {
    onClearOption() {
      this.$emit('clear-option');
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

  &__label {
    display: inline-block;
    vertical-align: middle;
    padding: 0.5rem;
  }

  &__clear {
    border: none;
    background: #eee;
    padding: 1.2rem;
    border-radius: 2px;
    float: right;

    &:hover {
      background: #ddd;
    }
  }
}
</style>
