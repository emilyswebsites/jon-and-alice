<template>
  <div class="rsvp__section">
    <div class="summary-row">
      <p class="summary-row__content"><em>{{ answers.names }}</em>
      <span v-if="answers.guests.length > 1">
        (<span v-for="(guest, index) in answers.guests" :key="guest.name">{{ guest.name }}{{ index === answers.guests.length - 1 ? '' : ', ' }}</span>)
      </span> accept{{ answers.invitationType === 'evening' ? '(s)' : (answers.guests.length > 1 ? "" : "s") }} with pleasure.</p>
      <button class="edit-button" @click="editStep('acceptance')"><img src="pencil.svg" alt="Edit acceptance" /></button>
    </div>
    <div v-for="(guest, index) in answers.guests" :key="`guest-${index}`" class="summary-row">
      <p class="summary-row__content">{{ answers.guests.length > 1 ? guest.name : "I" }}{{ guest.menuChoices.menuType === "child" ? " is 10 years or under and" : "" }} will have <em>{{ guest.menuChoices.starter }}</em>, followed by <em>{{ guest.menuChoices.main }}</em>, with <em>{{ guest.menuChoices.dessert }}</em> for dessert.</p>
      <button class="edit-button" @click="editMenuStep(index)"><img src="pencil.svg" :alt="`Edit ${guest.name}'s menu choice`" /></button>
    </div>
    <div class="summary-row">
      <div v-if="answers.dietaryRequirements" class="summary-row__content">
        <p>{{ answers.invitationType === 'evening' ? 'My/our' : (answers.guests.length > 1 ? "Our" : "My") }} dietary requirements are as follows:</p>
        <p class="dietary-requirements"><em>{{ answers.dietaryRequirements }}</em></p>
      </div>
      <p v-if="!answers.dietaryRequirements" class="summary-row__content">{{ answers.invitationType === 'evening' ? 'I/we' : (answers.guests.length > 1 ? "We" : "I") }} have no allergies or specific dietary requirements.</p>
      <button class="edit-button" @click="editStep('dietary')"><img src="pencil.svg" alt="Edit dietary requirements" /></button>
    </div>
    <button class="button" @click="submit()">Send!</button>
  </div>
</template>

<script>
export default {
  name: 'RsvpSummary',
  props: {
    answers: {
      type: Object,
      required: true,
    }
  },
  methods: {
    editStep(stepName) {
      this.$emit('edit-step', stepName);
    },
    editMenuStep(guestIndex) {
      this.$emit('edit-menu-step', guestIndex);
    },
    submit() {
      this.$emit('submit-rsvp');
    }
  }
}
</script>

<style scoped lang="scss">
.summary-row {
  display: flex;
  align-items: center;
  margin-top: 1.5rem;
  line-height: 1.4;

  @media screen and (max-width: 768px) {
    margin-top: 1rem;
  }

  p {
    margin: 0;
  }
}

.summary-row__content {
  flex-grow: 1;
  font-size: 1.25rem;

  @media screen and (max-width: 768px) {
    font-size: 1rem;
  }
}

em {
  font-style: normal;
  font-family: var(--font-heading);
  color: black;
}

.dietary-requirements em {
  margin-left: 2rem;
  display: block;

  @media screen and (max-width: 768px) {
    margin-left: 1rem;
  }
}

.edit-button {
  flex-grow: 0;
  flex-shrink: 0;
  border: 0;
  background: none;
  padding: 0;
  width: 1.5rem;
  height: 1.5rem;
  cursor: pointer;
  margin-left: 1.5rem;

  img {
    width: 100%;
    height: 100%;
    object-fit: contain;
    object-position: center;
  }
}

.button {
  margin: 2rem auto 0;
}
</style>
