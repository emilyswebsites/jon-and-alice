<template>
  <form class="rsvp__section" @submit.prevent="submit()">
    <label for="dietary-requirements">Please enter any dietary requirements below.</label>
    <textarea id="dietary-requirements" v-model="dietaryRequirements" name="dietary-requirements"></textarea>
    <p>If none of the menu options met your dietary requirements, we will work with the caterers to find an alternative for you.</p>
    <p>If you have any concerns, feel free to get in touch with us.</p>
    <button class="button">Continue</button>
  </form>
</template>

<script>
export default {
  name: 'RsvpDietaryRequirements',
  props: {
    oldDietaryRequirements: {
      type: String,
      default: '',
    }
  },
  data() {
    return {
      dietaryRequirements: '',
    }
  },
  created() {
    this.dietaryRequirements = this.oldDietaryRequirements;
  },
  methods: {
    submit() {
      this.$emit('set-dietary-requirements', this.dietaryRequirements);
    }
  }
}
</script>

<style scoped lang="scss">
.rsvp__section {
  > * {
    margin-top: 2rem;
  }
}

textarea {
  width: 100%;
  font-family: var(--font-heading);
  font-size: 1.25rem;
  padding: .25rem .75rem;
  height: 8rem;
  resize: none;
  border: 1px solid var(--clr-beige-medium);
  transition: border-color 150ms linear;

  &:focus {
    outline: none;
    border-color: var(--clr-beige-dark);
  }

  scrollbar-width: thin;
  scrollbar-color: var(--clr-green-medium) var(--clr-beige-light);

  &::-webkit-scrollbar {
    width: 8px;
  }

  &::-webkit-scrollbar-track {
    background: var(--clr-beige-light);
    border-radius: 20px;
  }

  &::-webkit-scrollbar-thumb {
    background-color: var(--clr-green-medium);
    border-radius: 20px;
  }
}

label, p {
  display: block;
  font-size: 1.25rem;
}

.button {
  margin: 2rem auto 0;
}
</style>
