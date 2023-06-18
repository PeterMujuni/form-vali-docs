<script setup lang="ts">

const props = defineProps({
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: Boolean
    },
    error: {
      type: String,
      default: ''
    },
    name: {
      type: String,
      default: ''
    }
})
</script>

<template>
    <input 
        v-bind="$attrs"
        :checked="modelValue"
        :id="name"
        type="checkbox"
        @change="$emit('update:modelValue', $event.target.checked)"
    />
    <label :for="name" v-if="label">{{ label }}</label>
</template>


<style scoped>

</style>