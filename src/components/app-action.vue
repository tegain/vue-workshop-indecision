<template>
  <button class="AppAction" :disabled="!hasOptions" @click="onPick">
    OK Google, choisis pour moi !
  </button>
</template>

<script>
export default {
  name: 'AppAction',

  props: {
    hasOptions: {
      type: Boolean,
      required: true
    }
  },

  methods: {
    onPick() {
      this.$emit('pick-option');
    }
  }
};
</script>

<style lang="scss">
.AppAction {
  display: block;
  width: 100%;
  padding: 2.4rem;
  margin: 2rem 0;
  border: none;
  background: #e91e63;
  border-radius: 2px;
  box-shadow: 0 2.4rem 1.2rem -1.2rem rgba(darken(#2c3e50, 15%), 0.4);
  text-align: center;
  font-size: 2.2rem;
  color: #fff;
  font-weight: bold;
  transition: background 0.3s, box-shadow 0.3s;

  &[disabled] {
    opacity: 0.5;
  }

  &:hover:not([disabled]) {
    background: darken(#e91e63, 5%);
    box-shadow: 0 1.8rem 1rem -1.2rem rgba(darken(#2c3e50, 15%), 0.4);
  }
}
</style>
