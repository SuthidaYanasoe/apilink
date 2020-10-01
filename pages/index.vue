<template lang="html">
  <div>
    <div>
      <v-text-field v-model="query" label="Search" />
      <v-btn color="cyan lighten-2" @click="handleSearchNasa">
        Search
      </v-btn>
    </div>
    <v-divider class="mt-2 mb-2" />
    <div v-for="list in nasa" :key="list.items">
      <!-- {{list}} -->
      <v-card
        class="mx-auto"
        max-width="400"
      >
        <nuxt-link :to=" {name: 'product-id', params: { id: list }} ">
          <img :src="list.links[0].href" height="300px" width="400">
          </v-img>
        </nuxt-link>
        <v-card-actions>
          <v-spacer />

          <v-btn icon color="pink">
            <v-icon>mdi-heart</v-icon>
          </v-btn>

          <v-btn icon color="indigo">
            <v-icon>mdi-bookmark</v-icon>
          </v-btn>

          <v-btn icon color="green">
            <v-icon>mdi-share-variant</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      query: '',
      nasa: ''
    }
  },
  methods: {
    handleSearchNasa () {
      const url = 'https://images-api.nasa.gov/search?q=' + this.query + ''
      axios.get(url).then((response) => {
        // eslint-disable-next-line no-console
        console.log(response.data.collection.items)
        this.nasa = response.data.collection.items.slice(0, 20)
      })
    }
  }
}
</script>
<style>
.theme--dark.v-application {
  background-image: url(https://media.giphy.com/media/TF14N5U5viSDC24n9B/giphy.gif);
  background-size: cover;
}
</style>
