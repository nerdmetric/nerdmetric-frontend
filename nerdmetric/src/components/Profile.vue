<template>
  <div id="profile">
    <img :src="userInfo.avatar" class="user-img"/>
    <h1>{{ userInfo.username }}</h1>
    <p>{{ userInfo.bio }}</p>

    <h3>Identifiers</h3>
    <table width=500 style="margin: 10px auto;" border="1px">
      <thead></thead>
      <tbody>
        <tr>
          <td align="left">ORCID</td>
          <td align="left"><a :href="userInfo.github_link">{{ userInfo.username }}</a></td>
        </tr>
        <tr>
          <td align="left">GitHub</td>
          <td align="left"><a :href="userInfo.github_link">{{ userInfo.username }}</a></td>
        </tr>
      </tbody>
    </table>

    <h3>Scraped Profiles</h3>
    <table width=500 style="margin: 10px auto;" border="1px">
      <thead></thead>
      <tbody>
        <tr>
          <td align="left">Publons</td>
          <td align="left"><a :href="userInfo.github_link">{{ userInfo.username }}</a></td>
        </tr>
      </tbody>
    </table>

    <div v-if="isAuthenticated">
      <!-- userInfo is a prop that was passed in from App -->
      <router-link
          class="btn btn-sm btn-outline-secondary action-btn"
          :to="{ name: 'settings' }">
          <i class="ion-gear-a"></i> Edit Profile Settings
      </router-link>
      <p>
        You are logged in. Try logging out to see what happens to this page.
      </p>

    </div>

    <div v-else>
      <h1>Error!</h1>
      <p>
        Please log in to see your profile
      </p>
    </div>

  </div>
</template>

<style>

</style>

<script>
export default {
  name: 'profile',
  data() {
    return {

    };
  },
  // the parent component feeds these vars to this component
  props: ['isAuthenticated', 'userInfo'],
};
</script>
