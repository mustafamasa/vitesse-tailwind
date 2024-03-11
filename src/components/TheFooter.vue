<script setup lang="ts">
import { availableLocales, loadLanguageAsync } from '~/modules/i18n'

const { t, locale } = useI18n()

async function toggleLocales() {
  const locales = availableLocales
  const newLocale = locales[(locales.indexOf(locale.value) + 1) % locales.length]
  await loadLanguageAsync(newLocale)
  locale.value = newLocale
}

const isDark = useDark()
</script>

<template>
  <nav class="flex gap-4 mt-6 justify-center text-xl">
    <RouterLink to="/" class="icon-btn" :title="t('button.home')">
      <i-carbon-campsite />
    </RouterLink>

    <button class="icon-btn" :title="t('button.toggle_dark')" @click="toggleDark()">
      <i-carbon-sun v-if="isDark" />
      <i-carbon-moon v-else />
    </button>

    <a class="icon-btn" :title="t('button.toggle_langs')" @click.prevent="toggleLocales()">
      <i-carbon-language />
    </a>

    <RouterLink to="/about" class="icon-btn" :title="t('button.about')" data-test-id="about">
      <i-carbon-dicom-overlay />
    </RouterLink>

    <a class="icon-btn" rel="noreferrer" href="https://github.com/antfu/vitesse" target="_blank" title="GitHub">
      <i-carbon-logo-github />
    </a>
  </nav>
</template>
