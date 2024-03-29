<template>
  <form class="rsvp__section" @submit.prevent="submit()">
    <p class="subtitle">Please let us know what you would like to eat. If you have any dietary requirements, these can be detailed on the next page.</p>
    <h3 class="guest-name linethrough"><span></span><span class="linethrough__content">{{ guest.name }}</span><span></span>
    </h3>
    <div class="menu">
      <div class="form-field form-field--radio">
        <label class="radio__label">Menu:</label>
        <div class="option">
          <input id="adult" v-model="menuType" value="adult" type="radio" name="menu-type" />
          <label for="adult">
            Full menu
          </label>
        </div>
        <div class="option">
          <input id="child" v-model="menuType" value="child" type="radio" name="menu-type" />
          <label for="child">
            Children's menu (10 years and under)
          </label>
        </div>
      </div>
      <div v-if="menuType" class="form-field form-field--radio">
        <label class="radio__label">Starter:</label>
        <div class="option">
          <input id="ham-hock" v-model="starter" value="ham hock and leek terrine" type="radio" name="starter" />
          <label for="ham-hock">Ham hock and leek terrine, served with toasted brioche</label>
        </div>
        <div class="option">
          <input id="bruschetta" v-model="starter" value="bruschetta" type="radio" name="starter" />
          <label for="bruschetta">Traditional bruschetta, crostini topped with chopped tomatoes and a basil oil dressing
            with mozzarella (V, VeO)</label>
        </div>
        <div v-if="menuType === 'child'" class="option">
          <input id="garlic-bread" v-model="starter" value="garlic bread" type="radio" name="starter" />
          <label for="garlic-bread">Garlic bread</label>
        </div>
        <div class="option">
          <input id="other-starter" v-model="starter" value="other" type="radio" name="starter" />
          <label for="other-starter">Other dietary requirements (please specify on next page)</label>
        </div>
      </div>
      <div v-if="menuType" class="form-field form-field--radio">
        <label class="radio__label">Main:</label>
        <div class="option">
          <input id="beef" v-model="main" value="roast sirloin of beef" type="radio" name="main" />
          <label for="beef">Traditional roast sirloin of beef with homemade Yorkshire pudding, roast potatoes and pan
            gravy (GF)</label>
        </div>
        <div class="option">
          <input id="chicken" v-model="main" value="chicken in white wine sauce" type="radio" name="main" />
          <label for="chicken">Breast of chicken served in a white wine sauce with asparagus on a bed of crushed new
            potatoes (GF)</label>
        </div>
        <div class="option">
          <input id="peppers" v-model="main" value="stuffed peppers" type="radio" name="main" />
          <label for="peppers">Peppers stuffed with vegetable risotto topped with parmesan shavings (GF, V, VeO)</label>
        </div>
        <div v-if="menuType === 'child'" class="option">
          <input id="nuggets" v-model="main" value="chicken nuggets" type="radio" name="main" />
          <label for="nuggets">Chicken nuggets, chips and beans</label>
        </div>
        <div class="option">
          <input id="other-main" v-model="main" value="other" type="radio" name="main" />
          <label for="other-main">Other dietary requirements (please specify on next page)</label>
        </div>
      </div>
      <div v-if="menuType" class="form-field form-field--radio">
        <label class="radio__label">Dessert:</label>
        <div class="option">
          <input id="toffee" v-model="dessert" value="sticky toffee pudding" type="radio" name="dessert" />
          <label for="toffee">Hot sticky toffee pudding with toffee sauce</label>
        </div>
        <div class="option">
          <input id="tart" v-model="dessert" value="lemon tart" type="radio" name="dessert" />
          <label for="tart">Tangy lemon tart with mango coulis</label>
        </div>
        <div v-if="menuType === 'child'" class="option">
          <input id="ice-cream" v-model="dessert" value="vanilla ice cream" type="radio" name="dessert" />
          <label for="ice-cream">Vanilla ice cream</label>
        </div>
        <div class="option">
          <input id="other-dessert" v-model="dessert" value="other" type="radio" name="dessert" />
          <label for="other-dessert">Other dietary requirements (please specify on next page)</label>
        </div>
      </div>
    </div>
    <button :class="{ 'button--disabled': !formValid }" type="submit" :disabled="!formValid"
      class="button">{{ isLastGuest ? 'Continue' : 'Next Guest' }}</button>
  </form>
</template>

<script>
export default {
  name: 'RsvpMenu',
  props: {
    guest: {
      type: Object,
      required: true,
    },
    isLastGuest: {
      type: Boolean,
      default: false,
    }
  },
  data() {
    return {
      menuType: '',
      starter: '',
      main: '',
      dessert: '',
    }
  },
  computed: {
    formValid() {
      return this.menuType
        && this.starter
        && this.main
        && this.dessert;
    }
  },
  watch: {
    guest: {
      immediate: false,
      handler (val, _oldVal) {
        this.populateChoices(val);
      }
    }
  },
  created() {
    this.populateChoices(this.guest);
  },
  methods: {
    populateChoices(guest) {
      this.menuType = guest.menuChoices.menuType ?? '';
      this.starter = guest.menuChoices.starter ?? '';
      this.main = guest.menuChoices.main ?? '';
      this.dessert = guest.menuChoices.dessert ?? '';
    },
    submit() {
      if (!this.formValid) {
        return;
      }

      this.$emit('set-menu-choices', { menuType: this.menuType, starter: this.starter, main: this.main, dessert: this.dessert });
    }
  }
}
</script>

<style scoped lang="scss">
.guest-name {
  margin-top: 2rem;

  * {
    font-family: var(--font-scripty);
  }

  @media screen and (max-width: 768px) {
    margin-top: 1rem;
  }
}

.form-field {
  align-items: center;
}

.form-field + .form-field {
  margin-top: 2rem;
}

.form-field--radio {
  display: block;

  .option {
    margin: .75rem 0;

    @media screen and (max-width: 768px) {
      margin: 0.5rem 0;
    }
  }
}

.menu {
  max-height: 14rem;
  overflow-y: auto;
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

.button {
  margin: 2rem auto 0;
}

.option label {
  min-width: 8rem;
}

@media screen and (max-width: 500px) {
  .subtitle {
    font-size: .85rem;
    font-family: var(--font-body);
    text-align: left;
  }

  .rsvp__section {
    padding: 0;
  }
}
</style>
