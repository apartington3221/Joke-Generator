<template>
    <div id="app">
      <h1>Random Joke</h1>
      <button @click="getJoke">Get a Joke</button>
      <p v-if="joke">{{ joke }}</p>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        joke: ''
      };
    },
    methods: {
      async getJoke() {
        try {
          const response = await axios.get('https://api.humorapi.com/jokes/random', {
            headers: {
              'x-api-key': 'bd0b86b9a80d416098266562654acf14'
            }
          });
          this.joke = response.data.joke;
        } catch (error) {
          console.error('Error fetching joke:', error);
        }
      }
    }
  };
  </script>
  
  <style scoped>
  #app {
    text-align: center;
    margin-top: 50px;
  }
  button {
    padding: 10px 20px;
    font-size: 16px;
  }
  </style>
  