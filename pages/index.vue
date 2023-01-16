<template>
  <div class="page">
    <div class="hero">
      <h1 class="hero__banner">
        <div class="hero__banner-content">
          <span class="hero__date linethrough"><span></span><span class="linethrough__content">13th May
              2023</span><span></span></span>
          <span class="hero__title">Alice & Jon</span>
          <span class="hero__subtitle linethrough"><span></span><span class="linethrough__content">are getting
              married</span><span></span></span>
        </div>
      </h1>
      <button class="scroll-button" @click="scrollPastHero()">
        <img src="down-arrow-circle.svg" alt="Scroll to schedule">
      </button>
      <p class="photo-credit">*Our photographer is Lisa - "Ampersand Memories"</p>
    </div>
    <TopMenu ref="menu" hide-title></TopMenu>
    <main>
      <section class="couples-note">
        <div class="card card--wide">
          <div class="card__inner-wrapper">
            <p>Hello family and friends,</p>
            <br>
            <p>We would love you to come and celebrate our wedding with us. Please RSVP before 31st March 2023.</p>
            <br>
            <p>Hope to see you soon!</p>
            <p>Alice & Jon</p>
            <NuxtLink to="rsvp" class="button">RSVP</NuxtLink>
          </div>
        </div>
      </section>
      <section>
        <h2 class="section-heading linethrough"><span></span><span
            class="linethrough__content">Schedule</span><span></span></h2>
        <div class="schedule__events">
          <div class="schedule__event">
            <div class="event__image framed-media">
              <img class="framed-media__content" src="photos/wedding-ring.jpg" alt="Wedding Ring">
            </div>
            <div class="event__text">
              <h3 class="event__heading">The Ceremony</h3>
              <div class="detail">
                <span class="detail__label">When:</span>
                <span class="detail__value">12:00</span>
              </div>
              <div class="detail">
                <span class="detail__label">Where:</span>
                <span class="detail__value">The Great Tythe Barn, Tetbury</span>
              </div>
              <p class="detail event__additional-info">
                Please arrive by 11:30 so you can be seated before the ceremony starts at 12:00. Summer formal dress
                code.
              </p>
            </div>
          </div>
          <div class="schedule__event">
            <div class="event__image framed-media">
              <img class="framed-media__content" src="photos/bouquet.jpg" alt="Wedding Ring">
            </div>
            <div class="event__text">
              <h3 class="event__heading">The Reception</h3>
              <div class="detail">
                <span class="detail__label">When:</span>
                <span class="detail__value">Following the ceremony</span>
              </div>
              <div class="detail">
                <span class="detail__label">Where:</span>
                <span class="detail__value">The Great Tythe Barn, Tetbury</span>
              </div>
              <p class="detail event__additional-info">
                Canapes, drinks and photos before the wedding breakfast.
              </p>
            </div>
          </div>
          <div class="schedule__event">
            <div class="event__image framed-media">
              <img class="framed-media__content" src="photos/champagne.jpg" alt="Wedding Ring">
            </div>
            <div class="event__text">
              <h3 class="event__heading">The Evening Party</h3>
              <div class="detail">
                <span class="detail__label">When:</span>
                <span class="detail__value">18:30</span>
              </div>
              <div class="detail">
                <span class="detail__label">Where:</span>
                <span class="detail__value">The Great Tythe Barn, Tetbury</span>
              </div>
              <p class="detail event__additional-info">
                Evening guests arrival between 18:30 & 19:00. Carriages at midnight.
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
  components: { TopMenu, PageFooter },
  methods: {
    scrollPastHero() {
      (this.$refs.menu as any).$el.scrollIntoView({ behavior: "smooth" });
    }
  }
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
  position: relative;
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

.scroll-button {
  position: absolute;
  bottom: 3rem;
  left: 50%;
  transform: translate(-50%);
  background: none;
  border: none;
  filter: drop-shadow(0px 0px 1px #81703840) drop-shadow(0px 0px 8px #81703820);
  cursor: pointer;

  img {
    width: 4rem;
    height: 4rem;
  }
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
  width: 36rem;
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
