<template>
  <div class="head_block">
    <AuthorTemplate></AuthorTemplate>
  </div>
</template>

<script>
import AuthorTemplate from './components/AuthorTemplate.vue'

export default {
  name: 'App',
  components: {
    AuthorTemplate
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
}

#app th {
  width: 100px;
  height: 50px;
}
</style>
