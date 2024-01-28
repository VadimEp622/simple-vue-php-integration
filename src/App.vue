<template>
  <div id="app">
    <input type="text" v-model="message" placeholder="Enter a message">
    <button @click="sendMessage">Send Message</button>
    {{ nodeEnv }}
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      message: '',
      nodeEnv: process.env.NODE_ENV
    };
  },
  methods: {
    async sendMessage() {
      try {
        const response = await axios.post('http://vue-php-integration-back.test/api.php', {
          message: this.message
        });

        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    }
  }
};
</script>