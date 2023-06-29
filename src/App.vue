<script setup lang="ts">
import { reactive } from 'vue'
import { RouterLink, RouterView } from 'vue-router'

const state = reactive<{
  aligns: 'left' | 'right'
  position: 'top' | 'bottom'
  width: string
  maxHeight: string
}>({
  aligns: 'right',
  position: 'bottom',
  width: '200px',
  maxHeight: 'auto'
})
</script>

<template>
  <header>
    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
    <puik-menu :align="state.aligns" :position="state.position">
      <template #trigger>
        <puik-button size="md">Show menu</puik-button>
      </template>

      <template #default="{ close }">
        <puik-menu-item-title> First section title </puik-menu-item-title>
        <puik-menu-item>
          <puik-button variant="text"> Item </puik-button>
        </puik-menu-item>
        <puik-menu-item>
          <puik-button variant="text" left-icon="home"> Item with icon </puik-button>
        </puik-menu-item>

        <puik-menu-item-separator />

        <puik-menu-item-title> Second section title </puik-menu-item-title>
        <p>Information text</p>
        <puik-menu-item>
          <puik-button variant="destructive" left-icon="delete" @click="close">
            Destructive item
          </puik-button>
        </puik-menu-item>
      </template>
    </puik-menu>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

nav {
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
  flex-grow: 1;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
