<template lang="html">
  <div v-if="film" id="filmDetail">
    <h1> {{film.title}} </h1>
    <h2>Directed by: {{film.director}} </h2>
    <h3>Episode ID: {{film.episode_id}}</h3>
    <h3>Release Date: {{film.release_date}}</h3>

    <div id="characterList">
      <character-list v-if="characters.length" :characters="characters"></character-list>

    </div>
  </div>
</template>

<script>
  import CharacterList from './CharacterList.vue';

  export default {
    name: 'film-detail',
    props: ['film'],
    components: {
      'character-list': CharacterList
    },
    data(){
      return {
        characters: []
      }
    },

    methods: {
      getCharacters() {
        const characterPromises = this.film.characters.map((characters) => {
          return fetch(characters).then(response => response.json())
        })
        Promise.all(characterPromises)
        .then(data => this.characters = data);
      }
    },

    mounted(){
      this.getCharacters();
    },

    watch: {
      film: function(){
        this.getCharacters();
      }
    }
  }
</script>

<style lang="css" scoped>
</style>
