<template>
  <div>
    <div class="hero">
      <h1 class="hero__banner">
        <span>13th May 2023</span>
        <span>Jon & Alice</span>
        <span>are getting married</span>
      </h1>
    </div>
    <TopMenu></TopMenu>
    <main>
      <section>
        <p>Hello friends and family,</p>
        <br>
        <p>We would love you to come and celebrate our wedding with us. Please RSVP before Xth Month YYYY.</p>
        <br>
        <p>See you soon!</p>
        <p>Alice & Jon</p>
        <button>RSVP</button>
      </section>
      <section>
        <h2>Schedule</h2>
        <div>
          <img src="photos/wedding-ring.jpg" alt="Wedding Ring">
          <h3>The Ceremony</h3>
          <div>
            <span>When:</span>
            <span>XX:00</span>
          </div>
          <div>
            <span>Where:</span>
            <span>A Part of Venue at The Great Tythe Barn, Tetbury</span>
          </div>
          <p>
            Any additional comments, such as please arrive early or make sure you’re wearing dungarees.
          </p>
        </div>
      </section>
    </main>
    <PageFooter></PageFooter>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import TopMenu from '~/components/TopMenu.vue';
import PageFooter from '~/components/PageFooter.vue';

export default Vue.extend({
    name: "IndexPage",
    components: { TopMenu, PageFooter }
})
</script>

<style scoped lang="scss">
  img {
    width: 20rem;
  }
</style>
