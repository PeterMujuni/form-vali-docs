<script setup lang="ts">
import { reactive } from 'vue'
import BaseInput from '../components/BaseInput.vue'
import BaseButton from '../components/BaseButton.vue'
import { useField, useForm } from 'vee-validate'

// DATA
const data = reactive({
  chooseOption: null,
  password: null,
})

const validation = {
    email: value => {
        if (!value) return 'This field is required'

        const regex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
        if (!regex.test(String(value).toLowerCase())) {
        return 'Please enter a valid email address'
        }

        return true
    },
    password: value => {
        const requiredMessage = 'This field is required'
        if(value === undefined || value === null) return requiredMessage
        if(!String(value).length) return requiredMessage

        return true
    }
}

// METHODS
const onSubmit = () => {
    alert('Submitted')
}

const { setFieldValue } = useForm({
    validationSchema: validation
})

const { value: email, errorMessage: emailError } = useField('email')
const { value: password, errorMessage: passwordError } = useField('password')

const changeHandler = (event) => {
    setFieldValue('email', event.target.value)
}

</script>

<template>
    <form @submit.prevent="onSubmit">
        <BaseInput 
            type="email" 
            label="Email" 
            name="email" 
            :error="emailError"
            :modelValue="email"
            @change="changeHandler"
        />
        <BaseInput 
            type="password" 
            label="Password" 
            name="password" 
            v-model="password"
            :error="passwordError"
        />
        <BaseButton type="submit">
            Submit
        </BaseButton>
    </form>
</template>



<style scoped>
    form {
        width: 550px;
        border: 1px solid black;
        padding: 1rem;
        margin: 2rem auto 0
    }
</style>