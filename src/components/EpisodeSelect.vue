<template lang="html">
  <div class="episode">
    <select @change="selectEpisode" v-model="episode">
      <option disabled value="">Select an Episode</option>
      <option v-for="episode in episodes" :value="episode">
          S{{ episode.season }}E{{ episode.episode }} - {{ episode.title }}
      </option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'episode-select',
  data() {
    return {
      episode: null
    }
  },
  props: ['episodes'],
  methods: {
    selectEpisode() {
      eventBus.$emit('episode-selected', this.episode);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
