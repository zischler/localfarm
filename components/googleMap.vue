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
		<div ref="infoWindow" v-show="showInfo" class="absolute w-full">
			<h3>{{infoTitle}}</h3>
			<p>{{infoText}}</p>
			Teaser
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			showInfo: false,
			infoTitle: "",
			infoText: "",
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
			}).then(() => {
				this.$refs.infoWindow.style.left = e.domEvent.target.getBoundingClientRect().left + "px";
				this.$refs.infoWindow.style.bottom = e.domEvent.target.getBoundingClientRect().top + "px";
			});
			this.infoTitle = marker.title;
			this.infoText = marker.text;
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