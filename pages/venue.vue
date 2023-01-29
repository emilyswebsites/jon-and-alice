<template>
  <div class="page">
    <TopMenu></TopMenu>
    <main>
      <h2 class="section-heading linethrough"><span></span><span class="linethrough__content">Venue</span><span></span>
      </h2>
      <div class="venue-content">
        <div class="details">
          <div class="detail">
            <div class="detail__label">Address:</div>
            <address class="detail__value">
              The Great Tythe Barn<br />
              Folly Farm, Long Newnton<br />
              Tetbury, Gloucestershire<br />
              GL8 8XA
            </address>
          </div>
          <div class="detail">
            <div class="detail__label">Website:</div>
            <div class="detail__value">
              <a target="_blank" href="https://www.gtb.co.uk">www.gtb.co.uk</a>
            </div>
          </div>
          <p class="detail">
            There is plenty of parking on site, and Tetbury is a 10-15 minute walk from the venue, via a footpath.
          </p>
        </div>
        <div class="map__container framed-media">
          <iframe class="map"
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2476.358040254779!2d-2.154304884258073!3d51.63496777965627!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x487172ee55b27ead%3A0x6c5b56a3197d7189!2sThe%20Great%20Tythe%20Barn!5e0!3m2!1sen!2sfr!4v1664546782684!5m2!1sen!2sfr"
            allowfullscreen="false" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
      </div>
    </main>
    <PageFooter></PageFooter>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import TopMenu from '~/components/TopMenu.vue';
import PageFooter from '~/components/PageFooter.vue';

export default Vue.extend({
  name: "VenuePage",
  components: { TopMenu, PageFooter }
})
</script>

<style scoped lang="scss">
main {
  display: flex;
  flex-direction: column;
}

.section-heading {
  margin-top: 2rem;
}

.venue-content {
  display: flex;
  padding: 4rem;
  height: 100%;
  flex-grow: 1;
  width: 60rem;
  max-width: 100%;
  margin: auto;
}

.details {
  flex: 1 1 0;
  align-self: center;
  padding-right: 4rem;
}

.detail + .detail {
  margin-top: 2rem;
}

.detail__label {
  width: 4rem;
}

.map__container {
  flex: 0 0 50%;
}

.map {
  width: 100%;
  height: 100%;
  min-height: 25rem;
  border: 6px solid transparent;
}

@media screen and (max-width:768px) {
  .venue-content {
    flex-direction: column;
  }

  .details {
    margin-bottom: 2rem;
    padding-right: 0;
  }
}

@media screen and (max-width:500px) {
  .venue-content {
    padding: 2rem;
  }
}
</style>
