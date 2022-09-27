<template>
  <div>
    <div class="hero">
      <h1 class="hero__banner">
        <div class="hero__banner-content">
          <span class="hero__date linethrough"><span></span><span class="linethrough__content">13th May 2023</span><span></span></span>
          <span class="hero__title">Alice & Jon</span>
          <span class="hero__subtitle linethrough"><span></span><span class="linethrough__content">are getting married</span><span></span></span>
        </div>
      </h1>
    </div>
    <TopMenu></TopMenu>
    <main>
      <section class="couples-note">
        <div class="card">
          <div class="card__inner-wrapper">
            <p>Hello friends and family,</p>
            <br>
            <p>We would love you to come and celebrate our wedding with us. Please RSVP before Xth Month YYYY.</p>
            <br>
            <p>See you soon!</p>
            <p>Alice & Jon</p>
            <NuxtLink to="rsvp" class="button">RSVP</NuxtLink>
          </div>
        </div>
      </section>
      <section>
        <h2 class="section-heading linethrough"><span></span><span class="linethrough__content">Schedule</span><span></span></h2>
        <div class="schedule__events">
          <div class="schedule__event">
            <div class="event__image framed-media">
              <img class="framed-media__content" src="photos/wedding-ring.jpg" alt="Wedding Ring">
            </div>
            <div class="event__text">
              <h3 class="event__heading">The Ceremony</h3>
              <div class="event__detail">
                <span class="detail__label">When:</span>
                <span class="detail__value">XX:00</span>
              </div>
              <div class="event__detail">
                <span class="detail__label">Where:</span>
                <span class="detail__value">A Part of Venue at The Great Tythe Barn, Tetbury</span>
              </div>
              <p class="event__additional-info">
                Any additional comments, such as please arrive early or make sure you’re wearing dungarees.
              </p>
            </div>
          </div>
          <div class="schedule__event">
            <div class="event__image framed-media">
              <img class="framed-media__content" src="photos/bouquet.jpg" alt="Wedding Ring">
            </div>
            <div class="event__text">
              <h3 class="event__heading">The Reception</h3>
              <div class="event__detail">
                <span class="detail__label">When:</span>
                <span class="detail__value">XX:00</span>
              </div>
              <div class="event__detail">
                <span class="detail__label">Where:</span>
                <span class="detail__value">A Part of Venue at The Great Tythe Barn, Tetbury</span>
              </div>
              <p class="event__additional-info">
                Any additional comments, such as please arrive early or make sure you’re wearing dungarees.
              </p>
            </div>
          </div>
          <div class="schedule__event">
            <div class="event__image framed-media">
              <img class="framed-media__content" src="photos/champagne.jpg" alt="Wedding Ring">
            </div>
            <div class="event__text">
              <h3 class="event__heading">The Evening Party</h3>
              <div class="event__detail">
                <span class="detail__label">When:</span>
                <span class="detail__value">XX:00</span>
              </div>
              <div class="event__detail">
                <span class="detail__label">Where:</span>
                <span class="detail__value">A Part of Venue at The Great Tythe Barn, Tetbury</span>
              </div>
              <p class="event__additional-info">
                Any additional comments, such as please arrive early or make sure you’re wearing dungarees.
              </p>
            </div>
          </div>
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
  padding: 4rem 2rem;
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
  text-align: center;
}

.hero__subtitle {
  font-family: var(--font-heading);
  font-size: 2rem;
}

.couples-note {
  padding: 4rem;
  width: 100%;
}

.card {
  margin: auto;
  text-align: center;
  max-width: 50rem;
  width: 100%;
  min-width: min-content;
  font-family: var(--font-scripty);
  font-size: 1rem;
  line-height: 1.6;

  p {
    margin: 0;
  }
}

.button {
  font-size: 1.25rem;
  margin: 2rem auto 0;
}

.schedule__events {
  width: 100%;
  padding: 4rem;
}

.schedule__event {
  display: flex;
  align-items: center;
  margin: auto;
  margin-bottom: 5rem;
  width: 50rem;
  max-width: 100%;
}

.event__image {
  width: 12rem;
  height: 12rem;
  flex-shrink: 0;
  flex-grow: 0;
}

.event__text {
  margin-left: 2rem;
}

.event__heading {
  font-family: var(--font-scripty);
  font-size: 1.5rem;
  margin: 0 0 1rem 0;
}

.event__detail {
  display: flex;
  margin-bottom: 1rem;
}

.detail__label {
  display: inline-block;
  width: 3rem;
  margin-right: 1rem;
}

.detail__value {

}

.event__additional-info {
  margin: 0;
}

@media screen and (max-width:768px) {
  .hero__title {
    font-size: 4rem;
  }

  .hero__date {
    font-size: 2rem;
  }

  .hero__subtitle {
    font-size: 1.5rem;
  }

  .schedule__events,
  .couples-note {
    padding: 4rem 2rem;
  }
}

@media screen and (max-width:500px) {
  .hero__title {
    font-size: 3rem;
  }

  .hero__date {
    font-size: 1.5rem;
  }

  .hero__subtitle {
    font-size: 1rem;
  }

  .button {
    font-size: 1rem;
  }

  .schedule__event {
    flex-direction: column;
  }

  .event__image {
    margin-bottom: 2rem;
  }

  .event__text {
    margin: 0;
  }

  .event__heading {
    text-align: center;
  }
}
</style>
