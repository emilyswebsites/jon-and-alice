<template>
  <div class="rsvp__section">
    <p>Thank you very much for your RSVP.</p>
    <p v-if="accepted">We look forward to seeing you on our special day!</p>
    <p v-else>Sorry you are unable to make it, but we are looking forward to seeing you in due course.</p>
  </div>
</template>

<script>
export default {
  name: 'RsvpComplete',
  props: {
    accepted: {
      type: Boolean,
      required: true,
    }
  },
  methods: {
    submit() {
      this.$emit('submit-rsvp');
    }
  }
}
</script>

<style scoped lang="scss">
.rsvp__section {
  max-width: 30rem;
}

p {
  font-size: 1.25rem;
  text-align: center;
  line-height: 1.6;
}
</style>
