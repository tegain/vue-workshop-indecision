<template>
  <div class="AppOptionsList">
    <div class="AppOptionsList__header">
      <h3 class="AppOptionsList__title">Mes options</h3>
      <button
        class="AppOptionsList__deleteAll"
        :disabled="optionsArrayEmpty"
        @click="onDeleteOptions"
      >
        Tout supprimer
      </button>
    </div>

    <div class="AppOptionsList__error" v-if="optionsArrayEmpty">
      Ajouter des options pour commencer
    </div>

    <ul class="AppOptionsList__list">
      <app-option
        v-for="(option, index) in options"
        :option="option"
        :key="index"
        :count="index + 1"
        @delete-option="onDeleteOption"
      />
    </ul>
  </div>
</template>

<script>
import AppOption from './app-option';

export default {
  name: 'AppOptionsList',

  components: {
    AppOption
  },

  props: {
    options: {
      type: Array,
      required: true
    }
  },

  computed: {
    optionsArrayEmpty() {
      return this.options.length === 0;
    }
  },

  methods: {
    onDeleteOptions() {
      this.$emit('delete-options');
    },

    onDeleteOption(option) {
      this.$emit('delete-option', option);
    }
  }
};
</script>

<style lang="scss">
.AppOptionsList {
  background: lighten(#2c3e50, 10%);

  &__header {
    display: flex;
    padding: 0 1.2rem;
    justify-content: space-between;
    background: lighten(#2c3e50, 5%);
  }

  &__title {
    color: #fff;
  }

  &__error {
    padding: 2rem;
    margin-top: 2rem;
    text-align: center;
    color: lighten(#2c3e50, 40%);
  }

  &__list {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  &__deleteAll {
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
