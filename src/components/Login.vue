<template>
 <div>
    <p>
      Vue + Vuex + Axios - User Registration and Login <br>
      Consume API from <a href="https://reqres.in/" target="_blank">REQ | RES</a>
    </p>

    <form class="login" @submit.prevent="login">
    <h1>Sign in</h1>

      <div class="form-group">
          <label for="email">E-mail</label>
          <input type="email" v-model="email" name="email" class="form-control" :class="{ 'is-invalid': submitted && !email }" required />
          <div v-show="submitted && !email" class="invalid-feedback">E-mail is required</div>
      </div>

      <div class="form-group">
          <label htmlFor="password">Password</label>
          <input type="password" v-model="password" name="password" class="form-control" :class="{ 'is-invalid': submitted && !password }" required />
          <div v-show="submitted && !password" class="invalid-feedback">Password is required</div>
      </div>

      <div class="form-group">
      <div class="alert alert-danger" v-if="error">{{ error }}</div>

          <button type="submit" class="btn btn-primary">Login</button>

          <router-link to="/register" class="btn btn-link">Register</router-link>
      </div>
    </form>
 </div>
</template>

<script>
export default {
  data () {
    return {
      email: '',
      password: '',
      submitted: false,
      error: false
    }
  },
  methods: {
    login: function () {
      let email = this.email
      let password = this.password
      this.$store.dispatch('login', { email, password })
        .then(() => this.$router.push('/'))
        .catch(() => this.loginFailed())
    },
    loginFailed () {
      this.error = 'Login failed!'
      delete localStorage.token
    }
  }
}
</script>

<style>
  .login {
    width: 50%;
    margin: 0 auto;
  }

  .form-group label {
    text-align: left;
    display: block;
  }
</style>
