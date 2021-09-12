<template>
	<div>
		<GmapMap
		:center="center"
		:zoom="13"
		map-type-id="terrain"
		class="w-full h-screen"
		ref="mapRef"
		:options="{
			zoomControl: true,
			mapTypeControl: false,
			scaleControl: false,
			streetViewControl: false,
			rotateControl: false,
			fullscreenControl: false,
			disableDefaultUi: false
		}">
			<GmapMarker
				:key="index"
				v-for="(m, index) in markers"
				ref="mapMarker"
				:position="m.position"
				:clickable="true"
				:draggable="true"
				:title="m.title"
				@click="toggleInfoWindow(m, $event)"
			/>
		</GmapMap>
		<div ref="infoWindow" v-show="showInfo" class="absolute top-16 left-1/2 w-full max-w-md transform -translate-x-1/2">
        	<FarmCard :farm="selectedFarm" :key="selectedFarm.id" :is-popup="true" @close="showInfo = false"/>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			showInfo: false,
			selectedFarm: {},
		}
	},
	mounted() {
		this.$refs.mapRef.$el.style.height = (window.innerHeight - this.$refs.mapRef.$el.getBoundingClientRect().top) + "px";
		this.locateGeoLocation();
	},
	props: {
		center: Object,
		markers: Array
	},
	methods: {
		toggleInfoWindow(marker, e) {
			this.$refs.mapRef.$mapPromise.then((map) => {
				map.panTo(marker.position)
			});
			this.selectedFarm = marker.farm;
			this.showInfo = true;
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