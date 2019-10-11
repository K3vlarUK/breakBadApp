<template lang="html">
  <div v-if="episode">
    <div class="episode-info">
      <h2>{{ episode.title }}</h2>
      <p><b>Season:</b> {{ episode.season }} - Episode: {{ episode.episode }}</p>
      <p><b>Date First Aired:</b> {{ episode.air_date }}</p>
      <h4><b>Characters Featured:</b></h4>
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

.episode-info ul {
  list-style: none;
  margin-top: -1rem;
  margin-left: -2.5rem;
}
</style>
