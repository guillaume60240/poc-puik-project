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
    | 'text'
  size: 'sm' | 'md' | 'lg'
  items: { label: string; to: string }[]
}>({
  disabled: false,
  variant: 'success',
  size: 'sm',
  items: [{ label: 'Home', to: '/' }]
})

function setVariant(e: any) {
  state.variant = e ? 'success' : 'warning'
}
</script>

<template>
  <main>
    <puik-breadcrumb :items="state.items" icon="home"></puik-breadcrumb>
    <puik-button left-icon="shopping_cart" :variant="state.variant">My button</puik-button>
    <puik-button right-icon="shopping_cart">My button</puik-button>
    <div>
      <PuikCheckbox
        label="label check box"
        :modelValue="true"
        @update:modelValue="setVariant($event)"
      ></PuikCheckbox>
    </div>
  </main>
</template>
