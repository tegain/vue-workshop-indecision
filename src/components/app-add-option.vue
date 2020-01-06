<template>
  <div class="AppAddOption">
    <div class="AppAddOption__error" v-if="error">{{ error }}</div>

    <form class="AppAddOption__form" @submit.prevent="onAddOption">
      <input
        v-model.trim="option"
        class="AppAddOption__input"
        type="text"
        name="option"
        placeholder="Ajouter une nouvelle option"
      />

      <button class="AppAddOption__submit" type="submit">Ajouter l'option</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'AppAddOption',

  props: {
    error: {
      type: String,
      default: null
    }
  },

  data() {
    return {
      option: ''
    };
  },

  methods: {
    onAddOption() {
      this.$emit('add-option', this.option);
      this.option = '';
    }
  }
};
</script>

<style lang="scss">
.AppAddOption {
  background: lighten(#2c3e50, 10%);
  padding: 1.2rem;

  &__error {
    border: 1px solid #e91e63;
    color: #e91e63;
    padding: 1.2rem;
    margin-bottom: 1.2rem;
  }

  &__form {
    display: flex;
    justify-content: space-between;
    width: 100%;
  }

  &__input {
    flex: 1;
    padding: 1.2rem;
    margin-right: 1.2rem;
    font-size: 1.6rem;
  }

  &__submit {
    padding: 1.2rem;
    border: none;
    background: #e91e63;
    border-radius: 2px;
    box-shadow: 0 2.4rem 1.2rem -1.2rem rgba(darken(#2c3e50, 15%), 0.4);
    text-align: center;
    font-size: 1.6rem;
    color: #fff;
    font-weight: bold;
    transition: background 0.3s, box-shadow 0.3s;

    &:hover {
      background: darken(#e91e63, 5%);
      box-shadow: 0 1.8rem 1rem -1.2rem rgba(darken(#2c3e50, 15%), 0.4);
    }
  }
}
</style>
