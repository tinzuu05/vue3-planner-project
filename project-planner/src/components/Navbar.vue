<template>
  <nav class="main-nav">
      <router-link :to="{name: 'Home' }">Projects</router-link>
      <router-link :to="{name: 'AddProject' }">Add a New Project</router-link>
  </nav>
</template>

<script>
export default {

}
</script>

<style>
    .main-nav {
        margin: 40px auto;
        text-align: center;
    }

    .main-nav a {
        display: inline-block;
        margin: 0 10px;
        text-decoration: none;
        color: #999;
        font-size: 18px;
    }

    a.router-link-active {
        padding-bottom: 4px;
        border-bottom: 2px solid #00ce89;
    }
</style>