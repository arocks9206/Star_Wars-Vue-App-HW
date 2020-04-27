<template lang="html">
  <form v-on:submit.prevent>
    <select v-on:change="handleSelect" v-model="selectedFilm">
      <option v-for="(film, index) in films" :value="film">{{film.title}}</option>
    </select>
  </form>
</template>

<script>
  import { eventBus } from '../main.js'

  export default {
    name: "film-filter-form",
    data(){
      return {
        "search": "",
        "selectedFilm": {},
      }
    },

    props: ["films"],
    methods: {
      handleSelect(){
        this.search = ""
        eventBus.$emit('film-selected', this.selectedFilm)
      }
    }
  } 
</script>

<style lang="css" scoped>
</style>
