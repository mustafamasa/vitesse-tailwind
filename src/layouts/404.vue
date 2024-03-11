<script setup lang="ts">
const router = useRouter()
const { t } = useI18n()
</script>

<template>
  <main class="px-16 py-40 text-center text-teal-700 dark:text-gray-200">
    <div class="text-4xl">
      <i class="inline-block" data-icon="carbon:warning" />
    </div>
    <RouterView />
    <div>
      <button class="text-sm btn m-3 mt-8" @click="router.back()">
        {{ t('button.back') }}
      </button>
    </div>
  </main>
</template>
