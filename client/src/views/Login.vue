<script>

export default {
  components: {

  },
  data() {
    return {
      password: '',
      username: ''
    }
  },
  emits: ['changePage', 'loginForm', 'Register'],
  methods: {
    loginForm(password, username) {
      this.$emit('loginForm', password, username)
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
        <h3 class="text-center">Login</h3>
      </div>
      <div class="card-body">
        <form v-on:submit.prevent="loginForm(password, username)">
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
          <p class="text-center"><small>Do not have an account?</small></p>
          <a class="text-center" href="#" @click.prevent="changePage('Register')"><small>Register</small></a><br><br>
          
          <button type="submit" class="btn btn-primary btn-block">Login</button>
        </form>
      </div>
    </div>
  </div>
</template>
  
<style>
.card {
  width: 400px;
  border-radius: 10px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

.card-header {
  background-color: #fff;
  border-bottom: none;
  text-align: center;
  padding: 20px 0px;
}

.btn-primary {
  background-color: #17a2b8;
  border-color: #17a2b8;
  font-weight: bold;
}

.btn-primary:hover {
  background-color: #138496;
  border-color: #138496;
}
</style>
  