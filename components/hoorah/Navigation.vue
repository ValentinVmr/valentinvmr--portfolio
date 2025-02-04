<script setup lang="ts">
const isMenuOpen = ref(false);
const { width } = import.meta.client ? useScreenSize() : { width: ref(0) };

function openMenu() {
  isMenuOpen.value = !isMenuOpen.value;
}

function handleClick() {
  isMenuOpen.value = false;
}

function isMobile() {
  return width.value < 680;
}

watch(width, (newValue, oldValue) => {
  isMenuOpen.value = isMenuOpen.value && newValue < 680;
})

</script>

<template>
  <nav class="navigation">
    <div class="navigation__container">
      <HoorahLogo class="navigation__container__logo"/>
      <IconBurgerMenu @click="openMenu()" class="burger-menu"/>
      <ul class="all-links" v-if="isMenuOpen || !isMobile()" :class="{ 'all-links--open': isMenuOpen && isMobile() }">
        <li><a @click="handleClick()" href="#about">À propos</a></li>
        <li><a @click="handleClick()" href="#skills">Compétences</a></li>
        <li><a @click="handleClick()" href="#projects">Projets</a></li>
        <li><a @click="handleClick()" href="#experiences">Expériences</a></li>
        <li><a @click="handleClick()" href="#contact">Contact</a></li>
      </ul>
    </div>
  </nav>
  <transition name="fade">
    <div class="background" v-if="isMenuOpen && isMobile()" @click="handleClick()"></div>
  </transition>
</template>

<style scoped lang="scss">
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.slide-leave-active,
.slide-enter-active {
  transition: 500ms ease-in-out;
}
.slide-enter {
  transform: translate(-100%, 0);
}
.slide-leave-to {
  transform: translate(100%, 0);
}

.burger-menu {
  cursor: pointer;

  @media screen and (min-width: 680px) {
    display: none;
  }
}

.background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 19;
}

.navigation {
  z-index: 20;
  position: sticky;
  top: 0;
  left: 0;
  border-bottom: 1px solid #E5E5E5;
  background: white;

  &__container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1280px;
    margin: 0 auto;
    height: 70px;
    padding: 0 1rem;

    @media screen and (min-width: 680px) {
      padding: 0 4rem;
    }

    &__logo {
      width: 100px;
    }

    ul {
      font-size: 0.875rem;

      @media screen and (min-width: 680px) {
        display: flex;
        gap: 1rem;
      }

      &.all-links {
        &--open {
          display: flex;
          flex-direction: column;
          position: absolute;
          top: 70px;
          right: 0;
          gap: 1rem;
          padding: 1rem;
          z-index: 20;
          background: white;
          height: 100vh;
          width: 240px;
        }
      }

      li {
        list-style: none;

        a {
          text-decoration: none;
          color: #121417;
          font-weight: 500;
        }
      }
    }
  }
}
</style>