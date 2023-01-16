<template>
  <div class="page">
    <TopMenu></TopMenu>
    <main>
      <section class="section">
        <h2 class="section-heading linethrough"><span></span><span
            class="linethrough__content">Accommodation</span><span></span></h2>
        <div class="section__content">
          <p class="section__description">There are various accommodation options on site, including self-catered
            cottages and B&Bs. Please note there are weddings on the days either side, and accommodation is not
            reserved.</p>
          <p class="section__description">There are various hotels, B&B's and cottage rentals within Tetbury and the
            surrounding Cotswold villages. Tetbury itself is just a 10/15 minute walk from the venue. Malmesbury is 10
            minutes away via car. There are also the larger towns of Stroud and Cirencester which are roughly a 25
            minute drive away.</p>
        </div>
      </section>
      <section class="section">
        <h2 class="section-heading linethrough"><span></span><span class="linethrough__content">Local Taxi
            Services</span><span></span></h2>
        <div class="section__content">
            <div class="card">
              <div class="card__inner-wrapper">
                <div class="detail">
                  <div class="detail__label">Pink Cabs (Tetbury):</div>
                  <div class="detail__value"><a href="tel:079 6003 6003">079 6003 6003</a></div>
                </div>
                <div class="detail">
                  <div class="detail__label">Abbey Taxis (Malmesbury):</div>
                  <div class="detail__value"><a href="tel:01666 823 366">01666 823 366</a></div>
                </div>
                <div class="detail">
                  <div class="detail__label">Reliance Taxis (Cirencester):</div>
                  <div class="detail__value"><a href="tel:07787 790644">07787 790644</a></div>
                </div>
              </div>
            </div>
          </div>
      </section>
      <section class="section">
        <h2 class="section-heading linethrough"><span></span><span
            class="linethrough__content">Gifts</span><span></span></h2>
        <div class="section__content">
          <p class="section__description">Your presence is present enough and we are lucky to have everything in our
            home that we need. But if you do wish to give, contributions to our honeymoon are always welcomed.</p>
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

.section__content {
  padding: 1rem 4rem 4rem;
  width: 60rem;
  max-width: 100%;
  margin: auto;
}

.section__description {
  margin: 0 0 1rem 0;
  line-height: 1.6;
}

.card {
  width: fit-content;
  margin: auto;
}

.detail:last-child {
  margin-bottom: 0;
}

.detail__label {
  width: 14rem;
}

.detail__value a {
  color: inherit;
}

@media screen and (max-width:600px) {
  .detail {
    flex-direction: column;
  }
}

@media screen and (max-width:500px) {
  .section__content {
    padding: 2rem;
  }
}
</style>
