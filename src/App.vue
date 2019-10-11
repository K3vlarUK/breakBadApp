<template lang="html">
  <div class="data">
    <div class="header">
      <h1>The Breaking Bad Compendium</h1>
    </div>
    <div class="data-container">
      <div class="episode-container">
        <div class="dropdown">
          <sub>Choose an episode to find out more about it</sub>
          <episode-select :episodes="episodes"></episode-select>
        </div>
        <div class="info-panel">
          <episode-details :episode="selectedEpisode"></episode-details>
        </div>
      </div>
      <div class="character-container">
        <div class="dropdown">
          <sub>Choose a character to find out more about them</sub>
          <character-select :characters="characters"></character-select>
        </div>
        <div class="info-panel">
          <character-details :character="selectedCharacter"></character-details>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import EpisodeSelect from './components/EpisodeSelect.vue';
import EpisodeDetail from './components/EpisodeDetail.vue';
import CharacterSelect from './components/CharacterSelect.vue';
import CharacterDetails from './components/CharacterDetail.vue';

export default {
  name: 'app',
  data() {
    return {
      episodes: [],
      selectedEpisode: null,
      characters: [],
      selectedCharacter: null,
      quotes: [],
      randomQuote: {}
    }
  },
  mounted() {
    fetch('https://www.breakingbadapi.com/api/episodes')
    .then(res1 => res1.json())
    .then(episodes => this.episodes = episodes)

    fetch('https://www.breakingbadapi.com/api/characters')
    .then(res2 => res2.json())
    .then(characters => this.characters = characters)

    fetch('https://breakingbadapi.com/api/quotes')
    .then(res3 => res3.json())
    .then(quotes => this.quotes = quotes)

    fetch('https://breakingbadapi.com/api/quote/random')
    .then(res4 => res4.json())
    .then(randomQuote => this.randomQuote = randomQuote)

    eventBus.$on('episode-selected', (episode) => {
      this.selectedEpisode = episode;
    })

    eventBus.$on('character-selected', (character) => {
      this.selectedCharacter = character;
    })
  },
  components: {
    "episode-select": EpisodeSelect,
    "episode-details": EpisodeDetail,
    "character-select": CharacterSelect,
    "character-details": CharacterDetails
  }
}
</script>

<style lang="css" scoped>
h1 {
  text-align: center;
}

.data-container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>
