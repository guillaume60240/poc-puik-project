<script setup lang="ts">
import { reactive } from 'vue'

const state = reactive<{
  disabled: boolean
  variant:
    | 'primary'
    | 'secondary'
    | 'tertiary'
    | 'destructive'
    | 'warning'
    | 'success'
    | 'info'
    | 'error'
    | 'text'
  size: 'sm' | 'md' | 'lg'
  items: { label: string; to: string }[]
}>({
  disabled: false,
  variant: 'success',
  size: 'sm',
  items: [
    { label: 'Home', to: '/' },
    { label: 'About', to: '/about' }
  ]
})
</script>

<template>
  <div class="about">
    <puik-breadcrumb :items="state.items" icon="home"></puik-breadcrumb>

    <h1>This is an about page</h1>
    <PuikProgressBar percentage="50"></PuikProgressBar>
    <puik-accordion-group contained="true">
      <puik-accordion title="Title 1" name="accordion-1" sub-title="subtitle">
        Content 1
      </puik-accordion>
      <puik-accordion name="accordion-2" title="Title 2"> Content 2 </puik-accordion>
      <puik-accordion title="Title 3" name="accordion-3"> Content 3 </puik-accordion>
    </puik-accordion-group>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
