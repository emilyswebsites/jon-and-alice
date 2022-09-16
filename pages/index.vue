<template>
  <div>
    <div class="hero">
      <h1 class="hero__banner">
        <div class="hero__banner-content">
          <span class="hero__date linethrough"><span></span><span class="linethrough__content">13th May 2023</span><span></span></span>
          <span class="hero__title">Jon & Alice</span>
          <span class="hero__subtitle linethrough"><span></span><span class="linethrough__content">are getting married</span><span></span></span>
        </div>
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
.hero {
  background-image: url(/photos/hero-image.jpg);
  background-position: center;
  background-size: cover;
  background-attachment: fixed;
  padding: 5rem 0;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  justify-content: center;
}

.hero__banner {
  padding: 4rem;
  background-color: var(--clr-beige-light-translucent);
  box-shadow: var(--shadow-subtle);
}

.hero__banner-content {
  margin: auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: fit-content;

  > * {
    line-height: 1;
  }
}

.hero__date {
  font-family: var(--font-heading);
  font-size: 3rem;
}

.hero__title {
  font-family: var(--font-scripty);
  font-size: 6rem;
  margin: 2rem 0;
}

.hero__subtitle {
  font-family: var(--font-heading);
  font-size: 2rem;
}

img {
  width: 20rem;
}
</style>
