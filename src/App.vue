<template lang="html">
  <div class="data">
    <div class="header">
      <h1>The Breaking Bad Compendium</h1>
    </div>
    <div class="random-quote">
      <h4>Your random quote:</h4>
      <random-quote :randomQuote="randomQuote"></random-quote>
    </div>
    <br>
    <div class="data-container">
      <div class="episode-container">
        <div class="dropdown">
          <h2>Episode Chooser</h2>
          <episode-select :episodes="episodes"></episode-select>
        </div>
        <div class="info-panel">
          <episode-details :episode="selectedEpisode"></episode-details>
        </div>
      </div>
      <div class="character-container">
        <div class="dropdown">
          <h2>Character Chooser</h2>
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
import RandomQuote from './components/RandomQuote.vue';

export default {
  name: 'app',
  data() {
    return {
      episodes: [],
      selectedEpisode: null,
      characters: [],
      selectedCharacter: null,
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
    "character-details": CharacterDetails,
    "random-quote": RandomQuote
  }
}
</script>

<style lang="css" scoped>
.data {
  font-family: helvetica;
}

.header {
  background: url('https://coverfiles.alphacoders.com/753/75395.jpg') 100% 100% no-repeat;
  padding: 4rem 4rem;
  margin-left: -7rem;
  margin-top: -1rem;
  width: 100vmax;
  height: 17vmax;
  border-bottom: 3px solid white;
}

.header h1 {
  text-align: center;
  font-size: 72px;
  font-family: helvetica;
  color: lightgrey;
  -webkit-text-stroke-width: 2px;
  -webkit-text-stroke-color: lightcyan;
}

.random-quote h4 {
  text-align: center;
  margin-bottom: -0.25rem;
  color: lightgrey;
  -webkit-text-stroke-width: 0.5px;
  -webkit-text-stroke-color: lightcyan;
}

.data-container {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

.episode-container {
  border: 2px solid black;
  border-radius: 20px;
  padding: 0 10rem 2rem;
  background-color: darkcyan;
  color: lightcyan;
  text-align: center;
}

.character-container {
  border: 2px solid black;
  border-radius: 20px;
  padding: 0 10rem 2rem;
  background-color: darkcyan;
  color: lightcyan;
  text-align: center;
}
</style>
