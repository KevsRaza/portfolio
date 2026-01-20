<template>
  <a
    :href="href"
    target="_blank"
    rel="noopener noreferrer"
    class="p-3 rounded-xl border transition-all hover:scale-105"
    :class="containerClass"
  >
    <component :is="icon" class="w-5 h-5 fill-current" />
  </a>
</template>

<script setup>
defineProps({
  href: {
    type: String,
    required: true
  },
  icon: {
    type: Object,
    required: true
  },
  containerClass: {
    type: String,
    required: true
  }
})
</script>
