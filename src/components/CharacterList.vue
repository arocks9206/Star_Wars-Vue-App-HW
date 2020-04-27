<template lang="html">
  <div v-if="characters" class="character-list">
    <h3>Character List</h3>
    <ul>
      <character-list-item v-for="(character, index) in characters" :key="index" :character="character"></character-list-item >
    </ul>
  </div>
</template>

<script>
  import CharacterListItem from './CharacterListItem'

  export default {
    name: 'character-list',
    props: ['characters'],
    components: {
      'character-list-item': CharacterListItem
    }
  }
</script>

<style lang="css" scoped>
.character-list-item {
  width: 100%;
  text-align: center;
}
</style>
