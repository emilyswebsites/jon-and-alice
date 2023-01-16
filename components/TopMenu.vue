<template>
  <header>
    <h1 v-if="!hideTitle" class="header__title">Alice & Jon</h1>
    <div class="mobile-header">
      <div class="mobile-header__dummy"></div>
      <img class="mobile-header__icon" src="a-and-j-icon.svg" alt="Alice & Jon">
      <button aria-label="Menu" class="menu-toggle-button" @click="toggleMenu">
        <svg class="menu-icon" viewBox="0 0 122.88 95.95" style="stroke:currentColor;fill:currentColor">
          <path style="fill-rule:evenodd;clip-rule:evenodd;"
            d="M8.94,0h105c4.92,0,8.94,4.02,8.94,8.94l0,0c0,4.92-4.02,8.94-8.94,8.94h-105C4.02,17.88,0,13.86,0,8.94l0,0 C0,4.02,4.02,0,8.94,0L8.94,0z M8.94,78.07h105c4.92,0,8.94,4.02,8.94,8.94l0,0c0,4.92-4.02,8.94-8.94,8.94h-105 C4.02,95.95,0,91.93,0,87.01l0,0C0,82.09,4.02,78.07,8.94,78.07L8.94,78.07z M8.94,39.03h105c4.92,0,8.94,4.02,8.94,8.94l0,0 c0,4.92-4.02,8.94-8.94,8.94h-105C4.02,56.91,0,52.89,0,47.97l0,0C0,43.06,4.02,39.03,8.94,39.03L8.94,39.03z" />
        </svg>
      </button>
    </div>
    <nav :class="{ open: showMenu }">
      <ul>
        <li>
          <NuxtLink class="link" to="/">Schedule</NuxtLink>
        </li>
        <li>
          <NuxtLink class="link" to="venue">Venue</NuxtLink>
        </li>
        <li>
          <NuxtLink class="link" to="other-info">Other Info</NuxtLink>
        </li>
        <li>
          <NuxtLink class="link" to="rsvp">RSVP</NuxtLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'TopMenu',
  props: {
    hideTitle: Boolean,
  },
  data() {
    return {
      showMenu: false,
    };
  },
  methods: {
    toggleMenu() {
      this.showMenu = !this.showMenu;
    }
  }
}
</script>

<style lang="scss">
header {
  position: sticky;
  top: 0;
  background-color: var(--clr-beige-light);
  box-shadow: var(--shadow-subtle);
  z-index: 10;
}

.header__title {
  font-family: var(--font-scripty);
  font-size: 2rem;
  padding: 1rem 1rem 0;
  margin: 0;
  text-align: center;
}

.mobile-header {
  display: none;
}

ul {
  list-style: none;
  display: flex;
  justify-content: center;
  margin: 0;
  padding: 1rem 0;
  background-color: var(--clr-beige-light);
}

li {
  padding: 0 2rem;
  text-align: center;

  &:not(:last-child) {
    position: relative;

    &::after {
      content: '';
      position: absolute;
      right: 0;
      top: 50%;
      transform: translateY(-50%);
      width: 6px;
      height: 6px;
      border-radius: 6px;
      background-color: var(--clr-beige-dark);
    }
  }
}

.link {
  font-family: var(--font-heading);
  color: var(--clr-beige-dark);
  text-decoration: none;
  text-align: center;
  font-size: 1.5rem;
  position: relative;

  &::before {
    content: '';
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    position: absolute;
    border: 1px solid var(--clr-beige-dark);
    border-width: 1px 0;
  }

  &:not(.nuxt-link-exact-active) {
    &::before {
      transition: transform 250ms ease-out, opacity 250ms ease-out;
      transform: scaleX(0);
      transform-origin: center;
      opacity: 0;
    }

    &:hover::before {
      transform: scaleX(1);
      opacity: 1;
    }
  }
}

@media screen and (max-width:768px) {
  header {
    padding: 1.5rem;
  }

  .header__title {
    display: none;
  }

  .mobile-header {
    display: flex;
    align-items: center;
  }

  .mobile-header__dummy {
    width: 1.5rem;
  }

  .mobile-header__icon {
    height: 3rem;
    padding: 0 1rem;
    flex-grow: 1;
  }

  .menu-toggle-button {
    display: flex;
    cursor: pointer;
    border: 0;
    background: none;
    padding: 0;
  }

  .menu-icon {
    width: 1.5rem;
    padding: 1rem 0;
    color: var(--clr-beige-dark);
  }

  nav {
    transform: scaleY(0);
    transform-origin: top;
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    background-color: var(--menu-colour);
    transition: transform 350ms ease-in-out;
    isolation: isolate;

    &::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 25%;
      box-shadow: var(--shadow-subtle);
      z-index: -1;
    }
  }

  nav.open {
    transform: scaleY(1);

    li {
      opacity: 1;
      transition: opacity 450ms ease-in-out 100ms;
    }
  }

  ul {
    flex-direction: column;
    align-items: center;
    padding: 1rem 1rem 1.5rem 1rem;
    margin: 0;
  }

  li {
    padding: 0;
    opacity: 0;
    transition: opacity 150ms linear;

    & + & {
      margin-top: 1rem;
    }

    &::after {
      display: none;
    }
  }

  .link {
    font-size: 1rem;
  }
}

@media screen and (max-width: 768px) {
  header {
    padding: 1rem;
  }

  .mobile-header__icon {
    height: 2rem;
  }

  .menu-icon {
    padding: .25rem 0;
  }
}
</style>
