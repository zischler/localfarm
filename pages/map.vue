<template>
  <div>
    <google-map :center="{lat: 47.5410808,lng: 7.5938071}" :markers="markers"></google-map>
  </div>
</template>

<script>
export default {
    data() {
        return {
            markers: []
        }
    },
    async mounted() {
        const farms = await this.fetchMockApi();
        for(let farm of farms) {
            let marker = {};
            marker.position = {lat: farm.lat, lng: farm.long};
            marker.title = farm.title;
            marker.farm = farm;
            this.markers.push(marker);
        }
    },
    methods: {
        async fetchMockApi () {
            let result = []
            await this.$axios.get(process.env.baseUrl)
            .then(response => {
                result = response.data
            })
            .catch(error => {
                console.error(error)
            })
            return result
        }
    }
}
</script>
<style>
html, body {margin: 0; height: 100%; overflow: hidden}
</style>