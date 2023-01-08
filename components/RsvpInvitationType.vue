<template>
  <div class="rsvp__section">
    <p class="subtitle">Get started by selecting your invitation type.</p>
    <div class="button-choice">
      <button class="button" @click="submitInvitationType('day')">Day</button>
      <button class="button" @click="submitInvitationType('evening')">Evening</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'RsvpInvitationType',
  methods: {
    submitInvitationType(choice) {
      this.$emit('invitation-selected', choice)
    }
  }
}
</script>

<style scoped lang="scss">
.button-choice {
  padding: 3rem 0rem 2rem;
  display: flex;
  justify-content: center;

  .button {
    width: 12rem;

    &:not(:last-child) {
      margin-right: 4rem;
    }
  }
}
</style>
