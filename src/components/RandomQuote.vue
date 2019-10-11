<template lang="html">
  <div class="quotation">
    <sub v-for="quote in randomQuote">
      <q>{{ quote.quote }}</q> - {{ quote.author }}
    </sub>
  </div>
</template>

<script>
export default {
  name: 'random-quote',
  props: ['randomQuote']
}
</script>

<style lang="css" scoped>
.quotation {
  text-align: center;
  margin-top: 0.5rem;
}

sub {
  padding: 0.4rem;
  border: 1px dotted black;
  border-radius: 25px;
}
</style>
