<template >
    <div class="container">
        <h1>Register</h1>
        <form @submit.prevent="saveData">
            <div class="mb-3">
                <label class="form-label">Username</label>
                <input type="text" class="form-control" id="name" name="name" v-model="users.name" />
            </div>
            <div class="mb-3">
                <label class="form-label">Email</label>
                <input type="email" class="form-control" id="email" name="email" v-model="users.email" />
            </div>
            <div class="mb-3">
                <label class="form-label">Password</label>
                <input type="password" class="form-control" id="password" name="password" v-model="users.password" />
            </div>
            <button type="submit" class="btn btn-dark">Submit</button>
        </form>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'Register',
    data() {
        return {
            result: {},
            users: {
                name: "",
                email: "",
                password: ""
            }
        }
    },
    created() { },
    mounted() {
        console.log("mounted....")
    },
    methods: {
        saveData() {
            axios.post("/register", this.users, {
                withCredentials: true,
            })
                .then(
                    ({ data }) => {
                        console.log("data", data)
                        try {
                            alert("register successfully")
                        } catch (error) {
                            alert("register failed")
                        }
                    }
                )
        }
    },
}
</script>
<style lang="">
    
</style>