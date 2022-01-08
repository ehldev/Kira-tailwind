<template>
	<header class="container border-solid border-b border-b-slate-200">
		<div class="grid grid-cols-6 text-center">
			<div class="flex flex-row justify-center items-center">
				<span class="icon d-inline-block" @click="showMenu = true">
                    <i class="fas fa-align-justify"></i>
                </span>
			</div>

			<div class="flex flex-row justify-center items-center">
				<span class="icon" :class="{'text-green-600': mostrarBuscador}" @click="mostrarBuscador = !mostrarBuscador">
                    <i class="fas fa-search"></i>
                </span>
			</div>

			<figure class="col-span-2 flex flex-row justify-center items-center">
				<img :src="appConfig.logo" alt="KiraSports" class="w-28" @click="$router.push('/')">
			</figure>

			<div class="flex flex-row justify-center items-center">
				<span class="icon d-inline-block">
                    <span class="icon d-inline-block">
	                    <i class="fas fa-user"></i>
	                </span>
                </span>
			</div>

			<div class="flex flex-row justify-center items-center" @click="mostrarCarrito = !mostrarCarrito">
				<i class="fas fa-shopping-cart" :class="{'text-green-600': mostrarCarrito}"></i>

                <span class="items-carrito d-inline-block bg-dark text-white px-2" >
                    5
                </span>
			</div>
		</div>

		<BuscadorMenu v-if="mostrarBuscador" />

		<CarritoMobile v-if="mostrarCarrito" />
	</header>
</template>

<script>
	import { appConfig } from '@/env'

	import BuscadorMenu from '@/components/globales/BuscadorMenu'
	import CarritoMobile from '@/components/globales/CarritoMobile'

	export default {
		data() {
			return {
				appConfig,
				mostrarBuscador: false,
				mostrarCarrito: false
			}
		},

		components: {
			BuscadorMenu,
			CarritoMobile
		}
	}
</script>

<style>
</style>