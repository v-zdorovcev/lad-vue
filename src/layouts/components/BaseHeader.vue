<script setup lang="ts">
import { NButton, NIcon, NLayoutHeader } from 'naive-ui'
import { MenuOutline } from '@vicons/ionicons5'
import { defineAsyncComponent } from 'vue'
import { useSidebarStore } from '~/stores/modules/sidebar'
import SearchQuoteField from '~/components/SearchQuoteField.vue'

const ThemeSwitcher = defineAsyncComponent(() => import('./ThemeSwitcher.vue'))

const sidebarStore = useSidebarStore()
</script>

<template>
  <NLayoutHeader class="header" bordered>
    <div class="header__container">
      <NButton circle quaternary type="tertiary" @click="sidebarStore.toggleDisplay">
        <NIcon size="22" :component="MenuOutline" />
      </NButton>

      <SearchQuoteField />

      <ThemeSwitcher />
    </div>
  </NLayoutHeader>
</template>

<style lang="css" scoped>
  .header {
    --header-height: 56px;
    --side-padding: 16px;

    position: sticky;
    top: 0;
    z-index: 50;
    align-items: center;
    display: grid;
    grid-template-rows: calc(var(--header-height) - 1px);
    padding: 0 var(--side-padding);
  }

  @media (min-width: 640px) {
    .header {
      --side-padding: 32px;
    }
  }

  .header__container {
    width: 100%;
    display: grid;
    grid-template-columns: auto 1fr auto;
    align-items: center;
    gap: 24px;
    height: 100%;
  }
</style>
