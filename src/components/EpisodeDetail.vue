<template lang="html">
  <div v-if="episode">
    <div class="episode-info">
      <h3>{{ episode.title }}</h3>
      <p>Season: {{ episode.season }} - Episode: {{ episode.episode }}</p>
      <p>Date First Aired: {{ episode.air_date }}</p>
      <h5>Characters Featured:</h5>
      <ul>
        <li v-for="character in episode.characters">
          {{ character }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'episode-details',
  props: ['episode']
}
</script>

<style lang="css" scoped>
.episode-info {
  margin-top: 1rem;
}
</style>
