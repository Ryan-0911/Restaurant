<template>
  <div class="nav">
    <router-link to="/">Home</router-link>
    <router-link to="/add">Add Restaurant</router-link>
    <a v-on:click="logout" ref="#">Logout</a>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Header",
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style>
.nav {
  background-color: #333;
  overflow: hidden;
}
.nav a {
  float: left;
  color: white;
  padding: 14px 16px;
  text-align: center;
  font-size: 16px;
  text-decoration: none;
  margin-right: 5px;
}

.nav a:hover {
  background: #ddd;
  color: #333;
}
</style>
