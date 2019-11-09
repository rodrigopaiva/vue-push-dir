<template>
  <div>
    <p>
      Vue + Vuex + Axios - User Registration and Login <br>
      Consume API from <a href="https://reqres.in/" target="_blank">REQ | RES</a>
    </p>

    <form class="register" @submit.prevent="register">
      <h1>Register</h1>

      <div class="form-group">
        <label for="email">E-mail Address</label>
        <input id="email" type="email" v-model="email" name="email" class="form-control" :class="{ 'is-invalid': submitted && !email }" required />
        <div v-show="submitted && !email" class="invalid-feedback">E-mail is required</div>
      </div>

      <div class="form-group">
        <label htmlFor="password">Password</label>
        <input id="password" type="password" v-model="password" name="password" class="form-control" :class="{ 'is-invalid': submitted && !password }" required />
        <div v-show="submitted && !password" class="invalid-feedback">Password is required</div>
      </div>

      <div class="form-group">
        <div class="alert alert-danger" v-if="error">{{ error }}</div>

        <button type="submit" class="btn btn-primary">Register</button>
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
    register: function () {
      let data = {
        email: this.email,
        password: this.password
      }
      this.$store.dispatch('register', data)
        .then(() => this.$router.push('/'))
        .catch(() => this.registerFailed())
    },
    registerFailed () {
      this.error = 'Register failed!'
      delete localStorage.token
    }
  }
}
</script>

<style>
  .register {
    width: 50%;
    margin: 0 auto;
  }

  .form-group label {
    text-align: left;
    display: block;
  }
</style>
