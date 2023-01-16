<template>
  <div class="page">
    <TopMenu></TopMenu>
    <main>
      <div class="card">
        <div class="card__inner-wrapper">
          <h2 class="section-heading linethrough"><span></span><span
              class="linethrough__content">RSVP</span><span></span></h2>
          <RsvpInvitationType v-if="currentStep === 'invitation'" @invitation-selected="setInvitationType($event)">
          </RsvpInvitationType>
          <RsvpAcceptance v-if="currentStep === 'acceptance'" :deadline="rsvpDeadline" :old-accept="answers.acceptance"
            :old-names="answers.names" @acceptance-selected="setAcceptance($event)"></RsvpAcceptance>
          <RsvpNames v-if="currentStep === 'names'" :old-names="answers.guests" @set-names="setNames($event)">
          </RsvpNames>
          <RsvpMenu v-if="currentStep === 'menu'" :guest="answers.guests[currentGuestIndex]"
            :is-last-guest="currentGuestIndex === answers.guests.length - 1 || hasReachedSummary" @set-menu-choices="setMenuChoices($event)">
          </RsvpMenu>
          <RsvpDietaryRequirements v-if="currentStep === 'dietary'"
            :old-dietary-requirements="answers.dietaryRequirements"
            @set-dietary-requirements="setDietaryRequirements($event)"></RsvpDietaryRequirements>
          <RsvpSummary v-if="currentStep === 'summary'" :answers="answers" @edit-step="editStep($event)"
            @edit-menu-step="editMenuStep($event)" @submit-rsvp="submitRsvp()"></RsvpSummary>
          <RsvpComplete v-if="currentStep === 'complete'" :accepted="answers.acceptance"></RsvpComplete>
          <RsvpError v-if="currentStep === 'error'" :answers="answers"></RsvpError>
        </div>
      </div>
    </main>
    <PageFooter></PageFooter>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import TopMenu from '~/components/TopMenu.vue';
import PageFooter from '~/components/PageFooter.vue';
import RsvpInvitationType from '~/components/RsvpInvitationType.vue';
import RsvpAcceptance from '~/components/RsvpAcceptance.vue';
import RsvpNames from '~/components/RsvpNames.vue';
import RsvpMenu from '~/components/RsvpMenu.vue';
import RsvpDietaryRequirements from '~/components/RsvpDietaryRequirements.vue';
import RsvpSummary from '~/components/RsvpSummary.vue';
import RsvpComplete from '~/components/RsvpComplete.vue';
import RsvpError from '~/components/RsvpError.vue';

export default Vue.extend({
  name: "RsvpPage",
  components: {
    TopMenu,
    PageFooter,
    RsvpDietaryRequirements,
    RsvpAcceptance,
    RsvpMenu,
    RsvpNames,
    RsvpSummary,
    RsvpComplete,
    RsvpError,
    RsvpInvitationType
  },
  data() {
    return {
      currentStep: "invitation",
      currentGuestIndex: 0,
      hasReachedSummary: false,
      answers: {
        invitationType: '',
        names: '',
        acceptance: undefined as unknown as boolean,
        guests: [] as any[],
        dietaryRequirements: '',
      }
    }
  },
  computed: {
    rsvpDeadline() {
      return (this as any).answers.invitationType === 'evening' ? '13th April 2023' : '31st March 2023';
    }
  },
  methods: {
    showStep(stepName: string) {
      this.currentStep = stepName;
    },
    setInvitationType(event: string) {
      this.answers.invitationType = event;
      this.showStep('acceptance');
    },
    setAcceptance(event: { acceptance: boolean, names: string }) {
      this.answers.acceptance = event.acceptance;
      this.answers.names = event.names;
      if (event.acceptance) {
        if (this.answers.invitationType === 'day') {
          this.showStep('names');
        } else if (this.hasReachedSummary) {
          this.showStep('summary');
        } else {
          this.showStep('dietary');
        }
      } else {
        this.submitRsvp();
      }
    },
    setNames(event: string[]) {
      if (this.hasReachedSummary) {
        event.forEach((name, index) => {
          this.answers.guests[index].name = name;
        });
        this.showStep('summary');
      } else {
        this.answers.guests = event.map(name => {
          return {
            name,
            menuChoices: {
              menuType: '',
              starter: '',
              main: '',
              dessert: '',
            }
          }
        });
        this.showStep('menu');
      }
    },
    setMenuChoices(event: { menuType: string, starter: string, main: string, dessert: string }) {
      this.answers.guests[this.currentGuestIndex].menuChoices.menuType = event.menuType;
      this.answers.guests[this.currentGuestIndex].menuChoices.starter = event.starter;
      this.answers.guests[this.currentGuestIndex].menuChoices.main = event.main;
      this.answers.guests[this.currentGuestIndex].menuChoices.dessert = event.dessert;

      if (this.hasReachedSummary) {
        this.showStep('summary');
      } else if (this.currentGuestIndex >= this.answers.guests.length - 1) {
        this.showStep('dietary');
      } else {
        this.currentGuestIndex++;
      }
    },
    setDietaryRequirements(event: string) {
      this.answers.dietaryRequirements = event;
      this.hasReachedSummary = true;
      this.showStep('summary');
    },
    editStep(stepName: string) {
      this.showStep(stepName);
    },
    editMenuStep(guestIndex: number) {
      this.currentGuestIndex = guestIndex;
      this.editStep('menu');
    },
    submitRsvp() {
      console.log("Submitting!");
      // TODO
      // Send an email
      // UI for 'sending in progress'
      this.showStep('complete')
      // this.showStep('error')
    }
  }
})
</script>

<style scoped lang="scss">
main {
  background-image: url("../static/photos/rsvp-image.jpg");
  background-size: cover;
  background-attachment: fixed;
  background-position: center;
  padding: 4rem;
  min-height: 100vh;
}

.card {
  max-width: 50rem;
  margin: auto;
}

.section-heading {
  margin: 0;
  padding: 0;
}

@media screen and (max-width:768px) {
  main {
    padding: 4rem 2rem;
  }
}
</style>

<style lang="scss">
.rsvp__section {
  max-width: 42rem;
  margin: auto;
  padding: 0 1rem;
}

.rsvp__form {
  margin: 4rem 0 0;

  .form-field + .form-field {
    margin-top: 3rem;
  }

  @media screen and (max-width: 768px) {
    margin: 2rem 0 0;

    .form-field + .form-field {
      margin-top: 2rem;
    }
  }
}

.button--rsvp {
  margin: 4rem auto 0;

  @media screen and (max-width: 768px) {
    margin-top: 2rem;
  }
}

.subtitle {
  font-family: var(--font-scripty);
  color: var(--clr-beige-dark);
  text-align: center;
  margin: 0;
}

.form-field {
  display: flex;
  align-items: baseline;

  @media screen and (max-width: 768px) {
    flex-direction: column;
  }

  label {
    margin-right: 1rem;
    font-size: 1.25rem;

    @media screen and (max-width: 768px) {
      font-size: 1rem;
    }
  }

  input[type=text],
  input[type=number] {
    border: 0;
    border-bottom: 1px solid var(--clr-beige-medium);
    padding: 0.25rem 0.25rem 0;
    outline: 0;
    font-family: var(--font-heading);
    font-size: 1.25rem;
    min-width: 0px;
    transition: border-color 150ms linear;
    max-width: 100%;

    &:focus {
      border-color: var(--clr-beige-dark);
    }
  }

  input[type=text] {
    flex-grow: 1;
    width: 100%;
  }

  input[type=number] {
    width: 3rem;

    @media screen and (max-width: 768px) {
      width: 100%;
      text-align: center;
    }
  }

  .radio__options {
    display: flex;
    align-items: center;

    .option {
      margin-left: 1rem;
      min-width: 12rem;
    }
  }

  .option {
    flex-grow: 1;

    input[type=radio] {
      overflow: hidden;
      opacity: 0;
      cursor: pointer;
      height: 0;
      width: 0;
      margin: 0;
      position: fixed;
      top: 0;

      + label {
        position: relative;
        padding-left: 2.125rem;
        cursor: pointer;
        display: inline-block;

        &::before {
          content: '';
          position: absolute;
          left: 0;
          top: 50%;
          transform: translateY(-50%);
          width: 1.125rem;
          height: 1.125rem;
          border: 1px solid var(--clr-beige-dark);
        }

        &::after {
          content: '';
          background-image: url("../static/checkmark.svg");
          background-size: contain;
          background-repeat: no-repeat;
          width: 1.5rem;
          height: 1.5rem;
          position: absolute;
          top: 50%;
          left: -2px;
          transition: opacity 250ms ease-in, transform 250ms ease-in;
          transform-origin: top;
        }
      }

      &:not(:checked) + label::after {
        opacity: 0;
        transform: scale(0) translateY(-50%);
      }

      &:checked + label {
        &::before {
          background-color: var(--clr-beige-light);
        }

        &::after {
          opacity: 1;
          transform: scale(1) translateY(-50%);
        }
      }
    }

    label {
      span {
        font-family: var(--font-scripty);
        font-size: 0.75em;
        margin-left: .25em;
      }
    }
  }
}
</style>
