<template>
  <div
    bg="white opacity-60"
    dark:bg="dark-700 opacity-60"
    h="full"
    filter="grayscale blur-md contrast-200"
  >
    <div
      data-tauri-drag-region
      class="titlebar"
    >
      <div
        id="titlebar-minimize"
        class="titlebar-button"
        @click="appWindow.minimize()"
      >
        <i-mdi:window-minimize />
      </div>
      <div
        id="titlebar-maximize"
        class="titlebar-button"
        @click="appWindow.toggleMaximize()"
      >
        <i-mdi:window-maximize />
      </div>
      <div
        id="titlebar-close"
        class="titlebar-button"
        @click="appWindow.close()"
      >
        <i-mdi:close />
      </div>
    </div>        
    <img
      class="center"
      alt="Vue logo"
      src="./assets/logo.png"
    >
    <div id="nav">
      <router-link to="/">
        Home
      </router-link> |
      <router-link to="/about">
        About
      </router-link>
    </div>
    <button
      class="icon-btn mx-2 !outline-none"
      @click="toggleDark()"
    >
      <i-carbon-moon v-if="isDark" />
      <i-carbon-sun v-else />
    </button>    

    <router-view />
  </div>
</template>

<script setup lang="ts">
import { appWindow } from "@tauri-apps/api/window";
import { isDark, toggleDark } from "./logic/dark";
</script>

<style>
html, body {
  height: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
#nav {
  color: #42b983;
}
.titlebar {
  height: 30px;
  /* background: #329ea3; */
  user-select: none;
  display: flex;
  justify-content: flex-end;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  }
.titlebar-button {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  width: 30px;
  height: 30px;
  }
.titlebar-button {
  background: #42b983;
  }
  .titlebar-button:hover {
  background: #338d65;
  }  
</style>
