<template>
	<!-- <section>
		{{ slug }}

		<pre>
			{{ producto }}
		</pre>
	</section> -->

	<section class="container product-slug animate__animated animate__fadeIn">
		<button type="button" class="py-3 px-3 border rounded">Tailwind</button>
        <div class="row">
            <div class="col-md-12 mt-3">
                <nav aria-label="breadcrumb">
                    <ol class="breadcrumb bg-transparent px-0">
                        <li class="breadcrumb-item small">
                            <nuxt-link to="/">Home</nuxt-link>
                        </li>
                        <li class="breadcrumb-item active small text-dark" aria-current="page">{{ producto ? producto.nombre : slug }}</li>
                    </ol>
                </nav>
            </div>

            <article class="col-md-9 px-lg-0" v-if="producto">
                <span class="icon d-inline-block ml-3" @click="sidebarProductoMobile = true" v-if="$route.name != 'productos-slug'">
                    <i class="fas fa-align-justify"></i>
                    Submenu
                </span>

                <!-- <informacion-producto :producto="producto"></informacion-producto> -->

                <pre>
                	{{ producto }}
                </pre>

                <section class="product-slug__tabs mt-5" v-if="producto.descripcionLarga">
                    <b-tabs content-class="mt-3">
                        <b-tab title="Descripción" active>
                            <section>
                            </section>
                        </b-tab>
                    </b-tabs>
                </section>
            </article>
        </div>
    </section>
</template>

<script>
	import GetGetProductoSlug from '@/graphql/productos/GetGetProductoSlug.gql'

	export default {
		data() {
			return {
				slug: this.$route.params.slug,
				// producto: null
			}
		},

		async asyncData(context) {
			let variables = {
				slug: context.params.slug
			}

	    	const response = await context.app.apolloProvider.defaultClient.query({
		                      query: GetGetProductoSlug,
		                      variables
		                    })

	    	let producto = response.data.GetGetProductoSlug

	    	if(producto.id) {
	    		return { producto }
	    	} else {
	    		context.error({ statusCode: 404, message: 'err message' })
	    	}
	    },

		mounted() {
			// this.getProduct()
		},

		methods: {
			/* async getProduct() {
		      let variables = {
		        "slug": this.slug
		      }

		      this.producto = await this.$apollo.query({
		                          query: GetGetProductoSlug,
		                          variables
		                        })
		    } */
		}
	}
</script>

<style>
</style>