<template>
  <div class="rsvp__section">
    <form class="rsvp__form" @submit.prevent="submit()">
      <div class="form-field">
        <label for="names">
          Number of guests attending:
        </label>
        <input id="guestCount" v-model="guestCount" type="number" min="1" max="9" name="guestCount"
          @blur="updateNumberOfGuests" />
      </div>
      <div v-for="(_guest, index) in guestNames" :key="index" class="guest">
        <h3 class="guest__heading">Guest {{ index + 1 }}</h3>
        <div class="form-field">
          <label :for="`guest-${index + 1}`">Name:</label>
          <input :id="`guest-${index + 1}`" v-model="guestNames[index]" type="text" name="guestName">
        </div>
      </div>
      <button class="button button--rsvp" :class="{ 'button--disabled': !formValid }" type="submit"
        :disabled="!formValid">Continue</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'RsvpNames',
  data() {
    return {
      guestCount: undefined,
      guestNames: [],
    }
  },
  computed: {
    formValid() {
      return +this.guestCount
        && !isNaN(+this.guestCount)
        && +this.guestCount > 0
        && this.guestNames.length === +this.guestCount
        && !this.guestNames.includes(undefined)
        && this.guestNames.filter(x => !x).length === 0;
    }
  },
  methods: {
    updateNumberOfGuests() {
      if (isNaN(+this.guestCount) || +this.guestCount <= 0) {
        return;
      }

      if (+this.guestCount < this.guestNames.length) {
        this.guestNames = this.guestNames.slice(0, this.guestCount);
      } else {
        while (+this.guestCount > this.guestNames.length) {
          this.guestNames.push('');
        }
      }
    },
    submit() {
      if (!this.formValid) {
        return;
      }

      this.$emit('set-names', this.guestNames);
    }
  }
}
</script>

<style scoped lang="scss">
.guest {
  margin-top: 2rem;
}

.guest__heading {
  font-family: var(--font-scripty);
  margin: 0;
}
</style>
