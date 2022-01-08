<template>
  <div>
    <HeaderMobile />

    <section class="container mx-auto px-4">
      <!-- <img :src="appConfig.logo" /> -->

      <Banner />
      
      <!-- <CarouselListaProductos /> -->

      <!-- <div class="grid grid-cols-1 sm:grid-cols-3 md:grid-cols-2 gap-4">
        <article class="bg-orange-200" v-for="p in productos">
          <nuxt-link :to="{name: 'productos-slug', params: {slug: p.slug}}">{{ p.nombre }}</nuxt-link>
        </article>
      </div> -->
    </section>
  </div>
</template>

<script>
import { appConfig } from '@/env'

import GetProductos from '@/graphql/productos/GetProductos.gql'

import HeaderMobile from '@/components/globales/HeaderMobile'
import Banner from '@/components/home/Banner'
import CarouselListaProductos from '@/components/productos/CarouselListaProductos'

export default {
  name: 'IndexPage',
  data() {
    return {
      appConfig,
      productos: []
    }
  },

  mounted() {
    this.getProducts()
  },

  components: {
    HeaderMobile,
    Banner,
    CarouselListaProductos
  },

  methods: {
    async getProducts() {
      let variables = {
        "number_paginate": 12,
        "page": 1,
        "estado": "1"
      }

      let response = await this.$apollo.query({
                          query: GetProductos,
                          variables
                        })

      this.productos = response.data.GetProductos.data
    }
  }
}
</script>