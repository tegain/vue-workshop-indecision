<template>
  <li class="AppOption">
    <span class="AppOption__label">{{ count }}. {{ option }}</span>
    <button class="AppOption__delete" @click="onDeleteOption">Supprimer</button>
  </li>
</template>

<script>
export default {
  name: 'AppOption',

  props: {
    option: {
      type: String,
      required: true
    },
    count: {
      type: Number,
      required: true
    }
  },

  methods: {
    onDeleteOption() {
      this.$emit('delete-option', this.option);
    }
  }
};
</script>

<style lang="scss">
.AppOption {
  display: flex;
  padding: 1.2rem;
  justify-content: space-between;
  align-items: center;
  color: #fff;

  &:not(:last-child) {
    border-bottom: 1px solid lighten(#2c3e50, 30%);
  }

  &__label {
    font-size: 1.8rem;
  }

  &__delete {
    align-self: center;
    padding: 1rem;
    border: none;
    background: none;
    font-size: 1.6rem;
    font-weight: bold;
    border-radius: 2px;
    color: lighten(#2c3e50, 40%);

    &[disabled] {
      opacity: 0.5;
    }

    &:hover:not([disabled]) {
      background: rgba(lighten(#2c3e50, 40%), 0.2);
    }
  }
}
</style>
