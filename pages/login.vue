<template>
  <b-card no-body>
    <b-tabs card>
      <b-tab title="Login" active>
        <Login />
      </b-tab>
      <b-tab title="Register" @click="$router.push('/register')"> </b-tab>
    </b-tabs>
  </b-card>
</template>

<script>
import Login from '@/components/Login'

export default {
  components: {
    Login,
  },
}
</script>

<style lang="scss" scoped></style>
