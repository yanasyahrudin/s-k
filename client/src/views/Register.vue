<script>
export default {
    data() {
        return {
            password: '',
            profileName: '',
            username: ''
        }
    },
    emits: ['changePage', 'Login', 'submitForm'],
    methods: {
        submitForm(password, profileName, username) {
            this.$emit('submitForm', password, profileName, username)
        },
        changePage(page) {
            this.$emit('changePage', page)
        }
    }
}
</script>

<template>
    <div class="container-fluid d-flex align-items-center justify-content-center vh-100">
        <div class="card">
            <div class="card-header">
                <h3 class="text-center">Register</h3>
            </div>
            <div class="card-body">
                <form v-on:submit.prevent="submitForm(password, profileName, username)">
                    <div class="form-group">
                        <label for="exampleInputProfileName1">Profile Name</label>
                        <input v-model="profileName" type="text" class="form-control" id="exampleInputProfileName1"
                            placeholder="Enter profile name">
                    </div>
                    <div class="form-group">
                        <label for="exampleInputUsername1">Username</label>
                        <input v-model="username" type="text" class="form-control" id="exampleInputUsername1"
                            placeholder="Enter username">
                    </div>
                    <div class="form-group">
                        <label for="exampleInputPassword1">Password</label>
                        <input v-model="password" type="password" class="form-control" id="exampleInputPassword1"
                            placeholder="Password">
                    </div>
                    <p class="text-center"><small>You have an account?</small></p>
                    <a class="text-center" href="#" @click.prevent="changePage('Login')"><small>Login</small></a><br><br>

                    <button type="submit" class="btn btn-primary btn-block">Register</button>
                </form>
            </div>
        </div>
    </div>
</template>

<style></style>