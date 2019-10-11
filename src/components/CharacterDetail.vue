<template lang="html">
  <div v-if="character">
    <div class="character-info">
      <img :src="character.img" :alt="character.name">
      <h2>{{ character.name }}</h2>
      <p><b>Nickname:</b> {{ character.nickname }}</p>
      <p><b>Status:</b> {{ character.status }}</p>
      <p><b>Played by:</b> {{ character.portrayed }}</p>
      <h4><b>Appears in:</b> </h4>
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

.character-info ul {
  list-style: none;
  margin-top: -1rem;
  margin-left: -2.5rem;
}
</style>
