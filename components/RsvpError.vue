<template>
  <div class="rsvp__section">
    <h3>Send us an email instead</h3>
    <p>Unfortunately, something went wrong while sending the RSVP. Don't worry though, you can directly send us an email
      with your responses using the button below.</p>
    <a class="button" :href="`mailto:${email}?subject=${subject}&body=${body}`">Open email client</a>
    <p>You can also copy your responses here: <button type="button" class="copy-link" :class="{ copied: copied }"
        @click="copyResponses()">Copy to clipboard</button></p>
  </div>
</template>

<script>
export default {
  name: 'RsvpError',
  props: {
    answers: {
      type: Object,
      required: true,
    }
  },
  data() {
    return {
      email: "aandjpresswedding@gmail.com",
      subject: '',
      body: '',
      copied: false,
      copyTimeout: null,
    }
  },
  created() {
    this.subject = encodeURIComponent(`RSVP - ${this.answers.invitationType} - ${this.answers.names}`);
    this.body = `${this.answers.names} ${this.answers.acceptance ? 'accept(s)' : 'decline(s)'}`;

    if (!this.answers.acceptance) {
      this.body = encodeURIComponent(this.body);
      return;
    }

    if (this.answers.invitationType === 'evening') {
      if (this.answers.dietaryRequirements) {
        this.body += `\n\nDietary requirements:\n\t${this.answers.dietaryRequirements}`;
      }
      this.body = encodeURIComponent(this.body);
      return;
    }

    this.answers.guests.forEach(guest => {
      this.body += `\n\n${guest.name}'s menu choices:\n\t${guest.menuChoices.menuType}\n\t${guest.menuChoices.starter}\n\t${guest.menuChoices.main}\n\t${guest.menuChoices.dessert}`;
    });

    if (this.answers.dietaryRequirements) {
      this.body += `\n\nDietary requirements:\n\t${this.answers.dietaryRequirements}`;
    }

    this.body = encodeURIComponent(this.body);
  },
  methods: {
    submit() {
      this.$emit('submit-rsvp');
    },
    async copyResponses() {
      clearTimeout(this.copyTimeout);
      this.copied = false;
      await navigator.clipboard.writeText(decodeURIComponent(this.body));
      this.copied = true;
      this.copyTimeout = setTimeout(() => { this.copied = false }, 15000);
    }
  }
}
</script>

<style scoped lang="scss">
h3 {
  font-family: var(--font-heading);
  font-size: 1.5rem;
}

p {
  font-size: 1.25rem;
  line-height: 1.6;
}

.button {
  width: fit-content;
}

.copy-link {
  border: 0;
  background: none;
  text-decoration: underline;
  font: inherit;
  color: inherit;
  position: relative;
  cursor: pointer;
}

.copied::after {
  content: 'Copied!';
  position: absolute;
  background: var(--clr-beige-light);
  border: 1px solid var(--clr-beige-medium);
  padding: .25rem 1rem;
  box-shadow: var(--shadow-subtle);
  top: 0;
  left: 0;
  transform: translateY(calc(-.5rem - 100%));
  animation: copied 15000ms normal forwards linear;
}

@keyframes copied {
  0% {
    opacity: 0;
  }

  1% {
    opacity: 1;
  }

  100% {
    opacity: 0;
  }
}
</style>
