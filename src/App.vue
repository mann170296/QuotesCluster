<template>
  <div class="container my-5">
    <app-new-quote @newQuoteAdded="addTheQuote"></app-new-quote>
    <app-quotes :quotes="quotes" @deleteQuote="deleteTheQuote"></app-quotes>
    <br><br>
    <div class="progress">
      <div class="progress-bar" role="progressbar" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"
          :style="{width: (quotes.length / maxQuoteLimit) * 100 + '%'}"
          :class="{'bg-warning': lengthMedium, 'bg-danger': lengthFull}">
         {{ quotes.length }} / {{ maxQuoteLimit }}
      </div>
    </div>

    <div class="alert alert-warning my-5">
      <b>PROTIP</b>: Click on a quote to delete it!
    </div>
  </div>
</template>

<script>
import NewQuote from './components/NewQuote'
import Quotes from './components/Quotes'

export default {
  name: 'App',

  components: {
    appQuotes: Quotes,
    appNewQuote: NewQuote
  },

  data() {
    return {
      quotes: [
        'An apple a day, keeps the doctor away'
      ],
      maxQuoteLimit: 10,
    }
  },

  methods: {
    addTheQuote(quote) {
      if(this.lengthFull) {
        return alert('You have reached quotes limit. Please delete some quotes to add more');
      }
      this.quotes.push(quote);
    },

    deleteTheQuote(index) {
      this.quotes.splice(index, 1);
    }
  },

  computed: {
    lengthMedium() {
      if(this.quotes.length >= 7) {
        return true;
      }
    },

    lengthFull() {
      if(this.quotes.length >= 10) {
        return true;
      }
    }
  }
}
</script>

<style>
</style>
