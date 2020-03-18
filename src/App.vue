<template>
  <div id="app">
    <quotes-counter
      :quoteCount="quotes.length"
      :maxQuotes="maxValue"
    ></quotes-counter>
    <new-quote @quoteAdded="addNewQuote"></new-quote>
    <grid-quotes>
      <div class="quote" v-for="(quote, index) in quotes" :key="index" @click="deleteQuote(index)">
        {{ quote }}
      </div>
    </grid-quotes>
  </div>
</template>

<script>
import GridQuotes from './components/GridQuotes.vue';
import QuotesCounter from './components/QuotesCounter.vue';
import NewQuote from './components/NewQuote.vue';

export default {
  name: 'App',
  components: {
    GridQuotes,
    QuotesCounter,
    NewQuote,
  },
  data: () => ({
    maxValue: 10,
    quotes: ['Start beautifull quote!', 'Test'],
  }),

  methods: {
    addNewQuote(quote) {
      this.quotes.length === this.maxValue
        ? alert(`It's no place for new quotes. Please delete old one!`)
        : this.quotes.push(quote);
    },

    deleteQuote(i) {
      this.quotes.splice(i, 1);
    }
  },
};
</script>

<style>
#app {
  margin: 40px;
}
</style>
