<template>
  <div class="rsvp__section">
    <p class="subtitle">Please reply before Xth Month 2023</p>
    <form class="rsvp__form" @submit.prevent="$emit('next-clicked')">
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
      <button class="button button--rsvp" :class="{ 'button--disabled': !names || accept === null }"
        type="submit" :disabled="!names || accept === null">Continue</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'RsvpAcceptance',
  data() {
    return {
      names: '',
      accept: null,
    }
  },
  methods: {
  }
}
</script>

<style scoped lang="scss">
.option {
  flex-grow: 1;

  input[type="radio"] {
    position: absolute;
    opacity: 0;
    cursor: pointer;
    height: 0;
    width: 0;

    + label {
      position: relative;
      padding-left: 28px;
      cursor: pointer;
      line-height: 20px;
      display: inline-block;

      &::before {
        content: '';
        position: absolute;
        left: 0;
        top: 0;
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
        bottom: -2px;
        left: -2px;
        transition: opacity 250ms ease-in, transform 250ms ease-in;
      }
    }

    &:not(:checked) + label::after {
      opacity: 0;
      transform: scale(0);
    }

    &:checked + label {
      &::before {
        background-color: var(--clr-beige-light);
      }

      &::after {
        opacity: 1;
        transform: scale(1);
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
</style>
