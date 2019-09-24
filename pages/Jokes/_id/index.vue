<template>
  <div>
    <nuxt-link to="/jokes">
      Back To Jokes
    </nuxt-link>
    <h2>
      {{ joke }}
    </h2>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      joke: {}
    }
  },
  async created () {
    const config = {
      headers: {
        'Accept': 'application/json'
      }
    }
    const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config)
    this.joke = res.data.joke
  },
  head () {
    return {
      title: this.joke,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Best place for corny dad jokes'
        }
      ]
    }
  }
}
</script>

<style scoped></style>
