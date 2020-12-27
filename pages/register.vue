<template>
  <b-card no-body>
    <b-tabs card>
      <b-tab title="Login" @click="$router.push('/login')"> </b-tab>
      <b-tab title="Register" active>
        <Register />
      </b-tab>
    </b-tabs>
  </b-card>
</template>

<script>
import Register from '@/components/Register'

export default {
  components: {
    Register,
  },
}
</script>

<style lang="scss" scoped></style>
