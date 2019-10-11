<template lang="html">
  <div>
    <select @change="selectCharacter" v-model="character">
      <option disabled value="">Select a Character</option>
      <option v-for="character in characters" :value="character">
        {{ character.name }}
      </option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js';

export default {
  name: 'character-select',
  data() {
    return {
      character: null
    }
  },
  props: ['characters'],
  methods: {
    selectCharacter() {
      eventBus.$emit('character-selected', this.character);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
