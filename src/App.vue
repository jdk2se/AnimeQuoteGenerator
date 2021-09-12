<template>
  <div class="app">
    <Header title="The Anime Quoter" />
    <Quote :quote="quote" />
    <div class="button-container">
      <button @click="getQuote">Generate</button>
    </div>

    <quote-list :quotes="quotes"></quote-list>
  </div>
</template>

<script>
import Header from '@/components/Header';
import Quote from '@/components/Quote';
import QuoteList from '@/components/QuoteList';

export default {
  name: 'App',
  components: {
    Header,
    Quote,
    QuoteList,
  },
  data() {
    return {
      quote: {},
      quotes: [],
    }
  },
  methods: {
    async getQuote() {
      if (this.quote.content) {
        this.quotes = [...this.quotes, this.quote];
      }

      const data = await fetch('https://animechan.vercel.app/api/random')
        .then(res => res.json());

      this.quote = {
        content: data.quote,
        anime: data.anime,
        character: data.character
      }
    },
  },
  mounted() {
    this.getQuote();
  }
}
</script>

<style lang="scss">
  :root {
    --primary: #d81e58;
    --secondary: #8a4fff;
    --tertiary: #32cbff;
    --dark: #131a26;
    --light: #eee;
    --grey: #848484;
  }

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Fira Sans', sand-serif;
  }

  .button-container {
    display: flex;
    justify-content: center;
    padding: 0 32px;
    margin: 64px auto;

    button {
      border: none;
      outline: none;
      background-color: var(--primary);
      padding: 16px 32px;
      border-radius: 99px;
      color: var(--light);
      font-size: 28px;
      font-weight: bold;
      text-transform: uppercase;
      cursor: pointer;
      transition: .4s;

      &:hover {
        background-color: var(--secondary);
      }
    }
  }
</style>
