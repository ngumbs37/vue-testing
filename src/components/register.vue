<template>
    <div id="app">

        <form @submit="validateForm" action="https://vuejs.org/" method="post">
            <div v-if="errors.length">
                <strong>Please correct the following error(s):</strong>
            <ul>
                <li :key="error" v-for="error in errors">{{  }}</li>
            </ul>
            </div>
            <label for="email">Email</label>
            <input v-model="email" type="text" id="email" name="email">

            <label for="username">Username</label>
            <input v-model="username" type="text" id="username" name="username">

            <label for="password">Password</label>
            <input v-model="password" type="text" id="password" name="password">

            <label for="passwordC">Confirm Password</label>
            <input v-model="passwordC" type="text" id="passwordC" name="passwordC">
            <br>
                <input type="submit" value="Submit" @submit="validateForm">
        </form>
    </div>
</template>

<script>
    export default {
        name: "register",
        data() {
            return {
                errors: [],
                email: null,
                username: null,
                password: null,
                passwordC: null
            }
        },
        methods: {
            validateForm: function(e) {
                const d = /^(([^<>()\\[\\]\\\\.,;:\\s@"]+(\\.[^<>()\\[\\]\\\\.,;:\\s@"]+)*)|(".+"))@((\\[[0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}\\.[0-9]{1,3}])|(([a-zA-Z\\0-9]+\\.)+[a-zA-Z]{2,}))$/;
                if (this.email && this.username && this.password && this.passwordC) {
                    return true
                }
                this.errors = [];
                d.test(this.email);
                if (!this.email)
                    this.errors.push('Email is required');
                if (!this.username)
                    this.errors.push('Username is required');
                if (!this.password.trim())
                    this.errors.push('Password is required');
                if (!this.passwordC.trim())
                    this.errors.push('Confirm Password is required');
                if (this.passwordC.trim() !== this.password.trim())
                    this.errors.push('Passwords do nnt match');
                e.preventDefault();
            }
        }
    }
</script>

<style>

</style>