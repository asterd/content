<template>
  <Dropdown v-if="availableLocales.length" class="flex">
    <template #trigger="{ open }">
      <button
        class="rounded-md hover:text-green-500 focus:outline-none focus:outline-none"
        :class="{ 'text-green-500': open }"
      >
        <icon-translate class="w-6 h-6" />
      </button>
    </template>

    <ul class="py-2">
      <li v-for="locale in availableLocales" :key="locale.code">
        <nuxt-link
          v-if="$i18n.locale !== locale.code"
          :to="switchLocalePath(locale.code)"
          class="flex px-4 items-center hover:text-green-500 leading-7"
        >{{ locale.name }}</nuxt-link>
      </li>
    </ul>
  </Dropdown>
</template>

<script>
export default {
  computed: {
    availableLocales () {
      return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale)
    }
  }
}
</script>
