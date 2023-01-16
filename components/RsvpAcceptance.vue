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
      <div class="form-field acceptance">
        <div class="option">
          <input id="accept" v-model="accept" :value="true" type="radio" name="accept" />
          <label for="accept">
            Accept <span>with pleasure</span>
          </label>
        </div>
        <div class="option">
          <input id="decline" v-model="accept" :value="false" type="radio" name="accept" />
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
    oldAccept: {
      type: Boolean,
      default: null,
    },
    oldNames: {
      type: String,
      default: '',
    },
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
  created() {
    this.accept = this.oldAccept;
    this.names = this.oldNames;
  },
  methods: {
    submit() {
      this.$emit('acceptance-selected', { acceptance: this.accept, names: this.names });
    }
  }
}
</script>

<style scoped lang="scss">
@media screen and (max-width: 768px) {
  .acceptance {
    flex-direction: column;

    .option + .option {
      margin-top: 1rem;
    }
  }
}
</style>
