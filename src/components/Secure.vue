<template>
  <div>
    <h1>This page is protected by auth</h1>

    <p>texto: {{ first_name }}</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      id: '',
      email: '',
      first_name: '',
      last_name: '',
      avatar: ''
    }
  },
  methods: {
    perfil: function () {
      let data = {
        id: this.id,
        email: this.email,
        first_name: this.first_name,
        last_name: this.last_name,
        avatar: this.avatar
      }
      this.$store.dispatch('perfil', data)
        .then(() => this.$router.push('/'))
    }
  }
}
</script>

<style></style>
