<template lang="html">
  <div v-if="character">
    <div class="character-info">
      <img :src="character.img" :alt="character.name">
      <h3>{{ character.name }}</h3>
      <p>Nickname: {{ character.nickname }}</p>
      <p>Status: {{ character.status }}</p>
      <p>Played by: {{ character.portrayed }}</p>
      <h5>Appears in: </h5>
      <ul>
        <li v-for="season in character.appearance">
          Season {{ season }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'character-details',
  props: ['character']
}
</script>

<style lang="css" scoped>
.character-info {
  margin-top: 1rem;
}

.character-info img {
  max-width: 200px;
  height: auto;
}
</style>
