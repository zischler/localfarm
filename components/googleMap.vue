<template>
	<GmapMap
	:center="center"
	:zoom="13"
	map-type-id="terrain"
	class="w-full h-screen"
	ref="mapRef"
	>
	<GmapMarker
		:key="index"
		v-for="(m, index) in markers"
		:position="m.position"
		:clickable="true"
		:draggable="true"
		@click="toggleInfoWindow(m)"
	/>
	</GmapMap>
</template>

<script>
export default {
	data() {
		return {
			showInfo: false,
		}
	},
	mounted() {
		this.$refs.mapRef.$el.style.height = (window.innerHeight - this.$refs.mapRef.$el.getBoundingClientRect().top) + "px";
		console.log(window.height - this.$refs.mapRef.$el.getBoundingClientRect().top);
		console.log(this.$refs.mapRef.$el.style.height);
		this.locateGeoLocation();
	},
	props: {
		center: Object,
		markers: Array
	},
	methods: {
		toggleInfoWindow(marker) {
			this.$refs.mapRef.$mapPromise.then((map) => {
				map.panTo(marker.position)
			});
			this.showInfo = true;
			console.log(marker.title);
		},

		locateGeoLocation: function() {
			navigator.geolocation.getCurrentPosition(res => {
				this.center = {
					lat: res.coords.latitude,
					lng: res.coords.longitude
				};
			});
		}
	}
}
</script>