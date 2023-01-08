<template>
  <div class="rsvp__section">
    <p class="subtitle">Please reply before {{ deadline }}.</p>
    <form class="rsvp__form" @submit.prevent="submit()">
      <div class="form-field">
        <label for="names">
          Name(s):
        </label>
        <input id="names" v-model="names" type="text" name="names" spellcheck="false" />
      </div>
      <div class="form-field">
        <div class="option">
          <input id="accept" v-model="accept" value="true" type="radio" name="accept" />
          <label for="accept">
            Accept <span>with pleasure</span>
          </label>
        </div>
        <div class="option">
          <input id="decline" v-model="accept" value="false" type="radio" name="accept" />
          <label for="decline">
            Decline <span>with regret</span>
          </label>
        </div>
      </div>
      <button class="button button--rsvp" :class="{ 'button--disabled': !names || accept === null }" type="submit"
        :disabled="!names || accept === null">Continue</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'RsvpAcceptance',
  props: {
    deadline: {
      type: String,
      required: true,
    }
  },
  data() {
    return {
      names: '',
      accept: null,
    }
  },
  methods: {
    submit() {
      this.$emit('acceptance-selected', { acceptance: this.accept, names: this.names });
    }
  }
}
</script>

<style scoped lang="scss">

</style>
