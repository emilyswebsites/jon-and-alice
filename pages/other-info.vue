<template>
  <div class="page">
    <TopMenu></TopMenu>
    <main>
      <section class="section">
        <h2 class="section-heading linethrough"><span></span><span class="linethrough__content">Accommodation</span><span></span></h2>
        <div class="section__content">
          <p class="section__description">There are various accommodation options on site, including self-catered cottages and B&Bs. Please note there are weddings on the days either side, and accommodation is not reserved.</p>
          <div class="card-grid">
            <div class="card">
              <div class="card__inner-wrapper">
                <h3 class="card__heading">A Nice Hotel</h3>
                <div class="detail">
                  <div class="detail__label">Website:</div>
                  <div class="detail__value">
                    <a target="_blank" href="https://example.com">a-nice-hotel.example.com</a>
                  </div>
                </div>
                <div class="detail">
                  <div class="detail__label">Address:</div>
                  <address class="detail__value">
                    A Nice Hotel, Road Name<br />
                    Tetbury<br />
                    P05T C0D3
                  </address>
                </div>
                <div class="card__description">Any additional comments, such as how far it is from the venue.</div>
              </div>
            </div>
            <div class="card">
              <div class="card__inner-wrapper">
                <h3 class="card__heading">Another Hotel</h3>
                <div class="detail">
                  <div class="detail__label">Website:</div>
                  <div class="detail__value">
                    <a target="_blank" href="https://example.com">a-nice-hotel.example.com</a>
                  </div>
                </div>
                <div class="detail">
                  <div class="detail__label">Address:</div>
                  <address class="detail__value">
                    A Nice Hotel, Road Name<br />
                    Tetbury<br />
                    P05T C0D3
                  </address>
                </div>
                <div class="card__description">Any additional comments, such as how far it is from the venue.</div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <section class="section">
        <h2 class="section-heading linethrough"><span></span><span class="linethrough__content">Local Taxi Services</span><span></span></h2>
        <div class="section__content">
          <div class="card-grid">
            <div class="card">
              <div class="card__inner-wrapper">
                <h3 class="card__heading">A Taxi Company</h3>
                <div class="detail">
                  <div class="detail__label">Phone:</div>
                  <div class="detail__value">01234 567890</div>
                </div>
                <div class="detail">
                  <div class="detail__label">Website:</div>
                  <div class="detail__value">
                    <a target="_blank" href="https://example.com">taxi.example.com</a>
                  </div>
                </div>
              </div>
            </div>
            <div class="card">
              <div class="card__inner-wrapper">
                <h3 class="card__heading">A Taxi Company</h3>
                <div class="detail">
                  <div class="detail__label">Phone:</div>
                  <div class="detail__value">01234 567890</div>
                </div>
                <div class="detail">
                  <div class="detail__label">Website:</div>
                  <div class="detail__value">
                    <a target="_blank" href="https://example.com">taxi.example.com</a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <section class="section">
        <h2 class="section-heading linethrough"><span></span><span class="linethrough__content">Gifts</span><span></span></h2>
        <div class="section__content">
          <p class="section__description">Lorem ipsum</p>
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

.detail {
  margin-top: 1rem;
}

.detail__label {
  width: 4rem;
}

.detail__value a {
  color: inherit;
}

@media screen and (max-width:768px) {

}

@media screen and (max-width:500px) {
  .section__content {
    padding: 2rem;
  }
}
</style>
