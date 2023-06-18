<script setup lang="ts">
const props = defineProps({
    label: {
        type: String,
        default: ''
    },
    name: {
        type: String,
        default: ''
    },
    modelValue: {
        type: [String, Number],
        default: ''
    },
    value: {
        type: [String, Number],
        default: ''
    },
    error: {
        type: String,
        default: ''
    }

})
</script>

<template>
    <label :for="name" v-if="label">{{ label }}</label>
    <input
        type="radio"
        v-bind="$attrs"
        :checked="modelValue === value"
        :id="name"
        :value="value"
        @change="$emit('update:modelValue', value)"
    />
</template>


<style scoped>

</style>