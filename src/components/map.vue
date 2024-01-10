<script setup>
	import {
		Loader
	} from "@googlemaps/js-api-loader"
</script>
<template>
	<div class="wrapper">
		<div class="map" id="map" ref="map"></div>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				map: null,
			}
		},
		async mounted() {
			const loader = new Loader({
				apiKey: "AIzaSyDTsVUorUw_8fDxu1TY1BLXjSH-BCTsQ8I",
				version: "weekly",
				// ...additionalOptions,
			});

			await loader.load();
			const { Map } = await google.maps.importLibrary("maps");

			this.map = new Map(this.$refs.map , {
				center: {
					lat: 21.03225,
					lng: 105.7460
				},
				zoom: 8,
			});
			console.log(this.map);
		},
	};
</script>

<style>
	body {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
	}

	.wrapper {
		width: 100%;
		height: 100vh;
		overflow: hidden;
		background: black;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.map {
		width: 1350px;
		height: 700px;
		background: gray;
	}
</style>