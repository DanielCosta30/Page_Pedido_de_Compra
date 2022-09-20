<template>


    <div id="nav">
      <router-link to="/">
        <img id="logo" :src="logo" :alt="alt">
      </router-link>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </div>


</template>

<script>

export default {
        name: 'NavB'

    }
</script>

<style scoped>


</style>