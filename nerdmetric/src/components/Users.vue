<template>
  <div id="search">
    <h1>Users</h1>
    <b-container>
      <b-row v-for="(user, index) in users" class="mt-2 mb-2" :key="index">
        <p>
          <router-link :to="'/view-user/' + user.name">
            {{user.name}}
          </router-link>
          <small>{{user.symbol}}</small>
        </p>
      </b-row>
      <b-row v-if="!users.length">
        No Coins Found
      </b-row>
      <b-row>
        <b-btn variant="outline-primary" class="mb-3" @click="incrementPage" v-if="!end">
          <span v-if="!loading">Next</span>
          <i class="fa fa-spinner fa-pulse" v-else></i>
        </b-btn>
      </b-row>
    </b-container>
  </div>
</template>

<style>
.articleSearch a {
  display: block;
}

.articleSearch {
  text-align: left;
}

#search {
  margin-top: 40px;
}
</style>

<script>
import axios from 'axios';

export default {
  name: 'Users',
  data() {
    return {
      users: [],
      query: null,
      start: 0,
      end: false,
      loading: true,
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    fetchData() {
      axios.get('https://api.coinmarketcap.com/v1/ticker/?limit=10')
      .then((resp) => {
        this.users = resp.data;
      })
      .catch(() => {
      });
    },
  },
};
</script>
