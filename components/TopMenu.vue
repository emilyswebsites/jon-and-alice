<template>
  <nav>
    <ul>
      <li><NuxtLink class="link" to="/">Schedule</NuxtLink></li>
      <li><NuxtLink class="link" to="venue">Venue</NuxtLink></li>
      <li><NuxtLink class="link" to="travel-and-accommodation">Travel & Accommodation</NuxtLink></li>
      <li><NuxtLink class="link" to="rspv">RSPV</NuxtLink></li>
    </ul>
  </nav>
</template>

<script>
  export default {
    name: 'TopMenu',
  }
</script>

<style lang="scss">
  ul {
    list-style: none;
    display: flex;
    justify-content: center;
    margin: 0;
    padding: 1rem 0;
    background-color: var(--clr-beige-light);
    box-shadow: var(--shadow-subtle);
  }

  li {
    padding: 0 2rem;

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

    &:not(.nuxt-link-active) {
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
</style>
