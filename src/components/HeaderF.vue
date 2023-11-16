<script>
import menuButtonImg from "../assets/logo.svg";
import iconMenu from "../assets/icon-menu.svg";
import iconCloseMenu from "../assets/icon-close-menu.svg";

import NavBar from "./NavBar.vue";

export default {
  data: function () {
    return {
      menuButtonImg,
      iconMenu,
      iconCloseMenu,
      toggleMainMenu: true,
    };
  },
  components: {
    NavBar
  },
  methods: {
    handleToggleMainMenu() {
      this.toggleMainMenu = !this.toggleMainMenu;
    },
  },
};
</script>

<template>
  <header>
    <div class="logo">
      <img src="../assets/logo.svg" alt="main logo" />
    </div>

    <div class="nav-bar">
      <NavBar />
    </div>

    <div class="dropdown-menu">
      <img class="icon-menu" v-if="toggleMainMenu === true" :src="iconMenu" alt="menu button" @click="this.handleToggleMainMenu"/>
    </div>

    <div v-if="!toggleMainMenu" class="mobile-drop-menu-content">
      <div class="mobile-menu-content-toggle" @click="this.handleToggleMainMenu"></div>
      <div class="mobile-menu-content">
        <header>
          <img class="icon-menu" :src="iconCloseMenu" alt="menu button" @click="this.handleToggleMainMenu"/>
        </header>

        <NavBar />
      </div>
    </div>
  </header>
</template>

<style>
.nav-bar {
  display: none;
}

header {
  box-sizing: border-box;
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 10px;
  height: 50px;
  width: 100%;
  z-index: 1;
}

.mobile-drop-menu-content {
  background: #00000075;
  position: absolute;
  height: 100vh;
  width: 100%;
  top: 0;
  left: 0;
  z-index: 2;
  display: flex;
  justify-content: flex-end;
}

.mobile-menu-content-toggle {
  width: 35%;
}

.mobile-menu-content {
  background: #ffffff;
  height: 100vh;
  width: 65%;
  display: flex;
  flex-direction: column;
}

.mobile-menu-content header {
  justify-content: flex-end;
}

.icon-menu {
  cursor: pointer;
}

@media (min-width: 1440px) {
  .nav-bar {
    display: flex;
  }

  .dropdown-menu, .mobile-drop-menu-content {
    display: none;
  }
}
</style>