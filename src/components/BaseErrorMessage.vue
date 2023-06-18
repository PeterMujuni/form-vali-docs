<script setup lang="ts">
const props = defineProps({
    id: {
      type: [String, Number],
      required: true
    }
})
</script>

<template>
  <p
    aria-live="assertive"
    class="errorMessage"
    :id="id"
  >
    <slot />
  </p>
</template>
