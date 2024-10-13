<template>
    <nav class="navbar">
      <ul class="navbar__menu">
        <li class="navbar__item" v-for="item in menuItems" :key="item.label">
          <a href="#" class="navbar__link">
            <i :data-feather="item.icon" class="navbar__icon"></i>
            <span class="navbar__label">{{ item.label }}</span>
          </a>
        </li>
      </ul>
    </nav>
  </template>
  
  <script>
  import feather from 'feather-icons'
  
  export default {
    name: "NavbarHome",
    data() {
      return {
        menuItems: [
          { label: "Home", icon: "home" },
          { label: "Messages", icon: "message-square" },
          { label: "Customers", icon: "users" },
          { label: "Projects", icon: "folder" },
          { label: "Resources", icon: "archive" },
          { label: "Help", icon: "help-circle" },
          { label: "Settings", icon: "settings" }
        ]
      }
    },
    mounted() {
      // Feather icons replace
      this.$nextTick(() => {
        feather.replace()
      })
    }
  }
  </script>
  

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;800&family=Poppins:wght@400;600;800&display=swap');

$borderRadius: 10px;
$spacer: 1rem;
$primary: #406ff3;
$text: #6a778e;
$linkHeight: $spacer * 3.5;
$timing: 250ms;
$transition: $timing ease all;

/* Font Setup */
body {
  background: #eaeef6;
  font-family: 'Poppins', sans-serif; /* Use Poppins for general text */
}

.navbar {
  position: fixed;
  top: $spacer;
  left: $spacer;
  background: #fff;
  border-radius: $borderRadius;
  padding: $spacer 0;
  box-shadow: 0 0 40px rgba(0, 0, 0, 0.03);
  height: calc(100vh - #{$spacer * 4});
  display: flex;
  flex-direction: column;
  align-items: center;

  &__menu {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  &__link {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    height: $linkHeight;
    width: $spacer * 5.5;
    color: $text;
    transition: $transition;
    font-family: 'Montserrat', sans-serif; /* Use Montserrat for links */

    span.navbar__label {
      position: absolute;
      left: 100%;
      transform: translate(-($spacer * 3));
      margin-left: 1rem;
      opacity: 0;
      pointer-events: none;
      color: $primary;
      background: #fff;
      padding: $spacer * 0.75;
      transition: $transition;
      border-radius: $borderRadius * 1.75;
      font-family: 'Poppins', sans-serif; /* Poppins for labels */
    }

    &:hover {
      color: #fff;
    }

    .navbar:not(:hover) &:focus,
    &:hover {
      span.navbar__label {
        opacity: 1;
        transform: translate(0);
      }
    }

    i.navbar__icon {
      font-size: 1.5rem;
    }
  }

  &__item {
    position: relative;

    &:hover::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: $primary;
      border-radius: $borderRadius * 1.75;
      z-index: -1;
      transition: $transition;
    }
  }
}

@keyframes gooeyEffect {
  0% {
    transform: scale(1, 1);
  }
  50% {
    transform: scale(0.5, 1.5);
  }
  100% {
    transform: scale(1, 1);
  }
}

.navbar__item:hover::before {
  animation: gooeyEffect $timing;
}

/* Responsive Design */
@media screen and (max-width: 768px) {
  .navbar {
    position: relative;
    height: auto;
    width: 100%;
    padding: $spacer;
    box-shadow: none;
  }

  .navbar__menu {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    width: 100%;
  }

  .navbar__link {
    width: auto;
    flex-direction: column;
    height: auto;
    span.navbar__label {
      position: static;
      transform: none;
      opacity: 1;
      margin-left: 0;
      pointer-events: auto;
      background: transparent;
      padding: 0;
    }
  }

  i.navbar__icon {
    font-size: 1.25rem;
  }
}

@media screen and (max-width: 480px) {
  .navbar__menu {
    flex-direction: column;
    width: 100%;
    align-items: center;
  }

  .navbar__link {
    width: 100%;
    justify-content: center;
    span.navbar__label {
      display: none;
    }
  }

  i.navbar__icon {
    font-size: 1rem;
  }
}
</style>
