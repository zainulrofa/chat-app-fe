<template >
    <div class="container">
        <h1>Login</h1>
        <form @submit.prevent="submitLogin">
            <div class="mb-3">
                <label for="exampleInputEmail1" class="form-label">Email address</label>
                <input type="email" class="form-control" id="exampleInputEmail1" v-model="form.email">
            </div>
            <div class="mb-3">
                <label for="exampleInputPassword1" class="form-label">Password</label>
                <input type="password" class="form-control" id="exampleInputPassword1" v-model="form.password">
            </div>
            <button type="submit" class="btn btn-dark">Submit</button>
        </form>
    </div>
</template>
<script setup>
import { ref } from 'vue';
import axios from 'axios';
import { useRouter } from 'vue-router';

const router = useRouter()

const form = ref({
    email: '',
    password: ''
})

const submitLogin = async () => {
    await axios.post('/login', {
        email: form.value.email,
        password: form.value.password
    })

    router.push('/')
}
</script>
<style lang="">
    
</style>