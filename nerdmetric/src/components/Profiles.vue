<template>
  <!-- This is a dynamic route
    Source: https://scotch.io/tutorials/getting-started-with-vue-router
  -->
  <div>
    <h1>{{ user.name }}</h1>

    <p>This is a dynamic route. The URL tells us which user we want to look up,
      and the vue component gets the info for that user</p>

    <p>ORCID: {{ user.symbol }}</p>
  </div>
</template>
<script>
  import axios from 'axios';

  export default {
    name: 'User',

    data() {
      return {
        user: {},
      };
    },

    created() {
      this.fetchData();
    },

    watch: {
      $route: 'fetchData',
    },

    methods: {
      fetchData() {
        axios.get(`https://api.coinmarketcap.com/v1/ticker/${this.$route.params.id}/`)
        .then((resp) => {
          this.user = resp.data[0];
        })
        .catch(() => {
        });
      },
    },
  };
</script>
