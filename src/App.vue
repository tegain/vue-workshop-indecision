<template>
  <div id="app">
    <app-header
      title="Indecision"
      subtitle="Put your life in the hands of the computer"
    />

    <div class="container">
      <app-action :has-options="options.length > 0" @pick-option="handlePick" />

      <app-selected-option
        :option="selectedOption"
        @clear-option="clearSelectedOption"
      />

      <app-options-list
        :options="options"
        @delete-option="handleDeleteOption"
        @delete-options="handleDeleteOptions"
      />

      <app-add-option :error="error" @add-option="handleAddOption" />
    </div>
  </div>
</template>

<script>
import AppHeader from './components/app-header';
import AppAddOption from './components/app-add-option';
import AppOptionsList from './components/app-options-list';
import AppSelectedOption from './components/app-selected-option';
import AppAction from './components/app-action';

export default {
  name: 'App',

  components: {
    AppHeader,
    AppAddOption,
    AppOptionsList,
    AppAction,
    AppSelectedOption
  },

  data() {
    return {
      options: [],
      selectedOption: null,
      error: null
    };
  },

  watch: {
    options(value) {
      if (value.length === 0) {
        localStorage.removeItem('options');
        return;
      }
      const options = JSON.stringify(value);
      localStorage.setItem('options', options);
    }
  },

  mounted() {
    try {
      const json = localStorage.getItem('options');
      const options = JSON.parse(json);

      if (options) {
        this.options = options;
      }
    } catch (e) {
      console.log(`
        Erreur lors de la récupération des options: ${e.message}
        Suppression du storage...
      `);
      localStorage.removeItem('options');
    }
  },

  methods: {
    handleAddOption(option) {
      if (!option) {
        this.error = 'Entrer une option valide';
        return;
      }

      if (this.options.includes(option)) {
        this.error = 'Cette option existe déjà !';
        return;
      }

      this.options.push(option);
    },

    handleDeleteOption(option) {
      this.options = this.options.filter(opt => opt !== option);
    },

    handlePick() {
      const randomNum = Math.floor(Math.random() * this.options.length);
      this.selectedOption = this.options[randomNum];
    },

    handleDeleteOptions() {
      this.options = [];
      this.clearSelectedOption();
    },

    clearSelectedOption() {
      this.selectedOption = null;
    }
  }
};
</script>
