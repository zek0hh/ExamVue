<template>
  <div id="nav">
    <b-nav align="center">
      <b-nav-item active><router-link to="/">Home</router-link></b-nav-item>
      <b-nav-item><router-link to="/about">About</router-link></b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  name: 'NavComponent',
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<!--
<style scoped>

</style>
-->
