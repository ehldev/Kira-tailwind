<template>
  <div class="container error text-center my-5">
    <img :src="logo" alt="Logo KiraSports" class="error__logo">

    <section class="mt-3">
        <h1 class="error__title font-weight-bold" v-if="error.statusCode === 404">Página no encontrada</h1>
        <h1 class="error__title font-weight-bold" v-else>Ocurrió un error</h1>
    </section>
    
    <div class="mt-3">
        <nuxt-link class="btn btn-outline-danger font-weight-bold rounded-0 px-4" to="/">Visitar tienda</nuxt-link>
    </div>
  </div>
</template>

<script>
  import { appConfig } from '@/env'

  export default {
    data() {
      return {
        logo: appConfig.logo
      }
    },
    layout: 'default',
    props: ['error']
  }
</script>

<style>
</style>