<template>
  <div id="app" class="container">
    <h1>Random Quote Generator</h1>
    <!-- display the quote or a loading message -->
    <p id="loading" v-if="loading">Loading...</p>
    <blockquote v-else>
      <p class="quote">"{{ quote }}"</p>
      <p class="author">&ndash; {{ author }}</p>
    </blockquote>
    <!-- button that triggers API call -->
    <button @click="getQuote">Get New Quote</button>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  data() {
    return {
      quote: '', // stores quote text
      author: '',
      loading: false // tracks loading status
    }
  },
  methods: {
    async getQuote() {
      this.loading = true
      try {
        // send GET request to Quotable API
        const response = await axios.get('https://quotes15.p.rapidapi.com/quotes/random/?language_code=en', {
          headers: {
            'x-rapid-api-host': 'quotes15.p.rapidapi.com',
            'x-rapidapi-key': 'bf63059798msh9641885127d8bdap1cebc1jsnfaf887995c25'
          }
        })
        //update the quote with the response data
        this.quote = response.data.content;
        this.author = response.data.originator.name;
      } catch (error) {
        console.error('Error fetching quote:', error)
        this.quote = 'Oops! Something went wrong.'
        this.author = ''
      } finally {
        this.loading = false
      }
    }
  },
  mounted() {
    // load a random quote when the app first starts
    this.getQuote()
  }
}
</script>

<style>

</style>