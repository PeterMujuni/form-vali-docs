<template>
    <label for="" v-if="label">{{label}}</label>
    <select 
        :class="{inputError: error}" 
        :value="modelValue" 
        v-bind="{
            ...$attrs, 
            onChange: ($event) => { $emit('update:modelValue', $event.target.value) }
        }"
    >
        <option
            v-for="option in options"
            :value="option"
            :key="option"
            :selected="option === modelValue"
        >
            {{ option }}
        </option>
    </select>
    <p
            v-if="error"
            class="errorMessage"
            :id="`${name}-error`"
            aria-live="assertive"
        >{{ error }}</p>
</template>

<script setup lang="ts">
const props = defineProps({
    label: {
        type: String,
        default: ''
    },
    modelValue: {
        type: String,
        default: ''
    },
    options: {
        type: Array,
        required: true
    },
    error: {
        type: String,
        default: ''
    }
})

</script>

<style lang="scss" scoped>
    label, select {
        display: block;
    }

    select {
        margin-bottom: 1rem;
        width: 100%;
        padding: 10px;

        &.inputError,
        &.inputError:active,
        &.inputError:focus {
            border-color: #ff3333;
        }
    }

    .errorMessage {
            color: #ff3333;
            margin: 0.3rem 0 0 0;
        }
</style>