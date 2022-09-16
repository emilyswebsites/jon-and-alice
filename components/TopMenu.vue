<template>
  <nav>
    <ul>
      <li><NuxtLink to="/">Schedule</NuxtLink></li>
      <li><NuxtLink to="venue">Venue</NuxtLink></li>
      <li><NuxtLink to="travel-and-accommodation">Travel & Accommodation</NuxtLink></li>
      <li><NuxtLink to="rspv">RSPV</NuxtLink></li>
    </ul>
  </nav>
</template>

<script>
  export default {
    name: 'TopMenu',
  }
</script>

<style lang="scss">
  .nuxt-link-active {
  }
</style>
