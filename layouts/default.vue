<template>
  <b-container fluid class="p-0">
    <Navigation />
    <b-container fluid class="pt-5">
      <b-row class="justify-content-center">
        <b-col cols="10" md="6">
          <Nuxt />
        </b-col>
      </b-row>
    </b-container>
  </b-container>
</template>

<style lang="scss">
*,
*::before,
*::after {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
