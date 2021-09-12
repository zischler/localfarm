<template>
<div>
	<div class="relative">
		<div class="max-w-5xl w-full mx-auto">
			<div class="w-full max-h-96 overflow-hidden flex items-center" v-if="farm.images">
				<img class="w-full" :src="farm.images" :alt="(farm.title) + ' image'">
			</div>
			<div class="p-4">
				<h1 class="text-3xl font-bold">{{farm.title}}</h1>
				<div class="mt-3 flex space-x-2 items-center">
					<svg
						width="30"
						height="30"
						viewBox="0 0 20 20"
						preserveAspectRatio="xMinYMax"
					>
						<use xlink:href="#clock"></use>
					</svg>
					<p>{{farm.opening_hours}}</p>
				</div>
				<div class="mt-6 w-full flex space-x-2 items-center justify-between">
					<div class="flex items-center">
						<svg
							width="30"
							height="30"
							viewBox="0 0 20 20"
							preserveAspectRatio="xMinYMax"
						>
							<use xlink:href="#map-pin-line"></use>
						</svg>
						<div>
							<p class="leading-3">{{farm.street}}, {{farm.zip}} {{farm.city}}</p>
							<a class="text-xs leading-3">-> Zur Kartenansicht</a>
						</div>
					</div>
					<div class="pl-4 bg-white flex justify-around space-x-2">
						<svg width="25" height="25" viewBox="0 0 20 20" preserveAspectRatio="xMinYMax">
							<use :xlink:href="'#'+farm.reachability"></use>
						</svg>
						<svg
							width="30"
							height="30"
							viewBox="0 0 20 20"
							preserveAspectRatio="xMinYMax"
						>
							<use xlink:href="#arrow-right-cycle"></use>
						</svg>
					</div>
				</div>
			</div>
		</div>
		<div class="absolute left-0 bottom-0 h-4 w-full z-10">
			<div class="max-w-5xl w-full mx-auto rounded-b-xl h-4 bg-white border-2 border-t-0 border-l-0 border-r-0 border-f-red"></div>
		</div>
		<div class="absolute left-0 -bottom-1 h-4 w-full -z-10">
			<div class="max-w-5xl w-full mx-auto rounded-b-xl h-4 bg-f-red-light border-2 border-t-0 border-l-0 border-r-0 border-f-red"></div>
		</div>
	</div>

	<div class="relative">
		<div class="max-w-5xl w-full mx-auto mb-6">
			<div class="p-4">
				<h1 class="text-2xl">Was dich erwartet</h1>
				<p>{{farm.content_text}}</p>
				<!-- TODO add wanderweg link-->
			</div>
		</div>
		<div class="absolute left-0 bottom-0 h-4 w-full z-10">
			<div class="max-w-5xl w-full mx-auto rounded-b-xl h-4 bg-white border-2 border-t-0 border-l-0 border-r-0 border-f-red"></div>
		</div>
		<div class="absolute left-0 -bottom-1 h-4 w-full -z-10">
			<div class="max-w-5xl w-full mx-auto rounded-b-xl h-4 bg-f-red-light border-2 border-t-0 border-l-0 border-r-0 border-f-red"></div>
		</div>
	</div>
	<div class="max-w-5xl w-full mx-auto">
		<div class="p-4 pt-0">
			<h1 class="text-2xl">Weitere Infos</h1>
			<p class="max-w-3xl mb-6">{{farm.info_text}}</p>
			<template v-if="farm.email">
				<div class="flex space-x-2 items-center mb-4">
					<svg
						width="30"
						height="30"
						viewBox="0 0 20 20"
						preserveAspectRatio="xMinYMax"
					>
						<use xlink:href="#globe"></use>
					</svg>
					<a :href="'mailto:'+farm.email">{{farm.email}}</a>
				</div>
			</template>
			<template v-if="farm.tel">
				<div class="flex space-x-2 items-center mb-4">
					<svg
						width="30"
						height="30"
						viewBox="0 0 20 20"
						preserveAspectRatio="xMinYMax"
					>
						<use xlink:href="#phone-call"></use>
					</svg>
					<a :href="'tel:'+farm.tel">{{farm.contact_person}} - {{farm.tel}}</a>
				</div>
			</template>
		</div>
	</div>
</div>
</template>

<script>
export default {
	name: "Farm-Detail-Page",
	data() {
		return {
			farm: {}
		}
	},
    async asyncData({ params }) {
		const id = params.farm;
		return { id }
    },
	async mounted() {
		const results = await this.$axios.get(process.env.baseUrl)
		.then(response => {
			return response.data
		})
		.catch(error => {
			console.error(error)
		});
		this.farm = results.find(farm => farm.id === +this.id);
	}
}
</script>