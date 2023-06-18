<template>
    <div class="form-wrapper">    
        <label :for="name" v-if="label">{{label}}</label>
        <input 
            v-bind="$attrs"
            :class="{inputError: error}" 
            :value="modelValue"
            :id="name"
            :placeholder="placeHolder"
            @input="$emit('update:modelValue', $event.target.value)"
            :aria-describedby="error ? `${name}-error` : null"
            :aria-invalid="error ? true : null"
        />
        <p
            v-if="error"
            class="errorMessage"
            :id="`${name}-error`"
            aria-live="assertive"
        >{{ error }}</p>
    </div>
</template>

<script setup lang="ts">
const props = defineProps({
    modelValue: {
        type: [String, Number],
        default: ''
    },
    label: {
        type: String,
        default: ''
    },
    name: {
        type: String,
        default: ''
    },
    placeHolder: {
        type: String,
        default: ''
    },
    error: {
        type: String,
        default: ''
    }
})
</script>

<style lang="scss" scoped>
    .form-wrapper {
        margin-bottom: 1rem;
        input, label {
            display: block
        }

        input {
            width: 100%;
            padding: 10px;
            border-radius: 4px;
            border: 1px solid grey;
            outline: none;

            &:focus {
                border-color: blue;
            }

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
    }
</style>