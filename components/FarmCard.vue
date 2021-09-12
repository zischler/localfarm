<template>
    <div class="flex flex-col rounded-lg shadow-lg overflow-hidden border border-gray-200 my-8 relative">
        <a :href="'/detail/'+farm.id" class="flex-shrink-0">
            <img class="h-48 w-full object-cover" :src="farm.images" alt="">
        </a>
        <div class="bg-white p-6 flex flex-row justify-between">
            <div class="flex flex-col">
                <a :href="'/detail/'+farm.id">
                    <h1 class="text-xl mb-2 font-semibold text-gray-900">{{ farm.title }}</h1>
                </a>
                <p class="text-sm font-medium text-gray-500 flex">
                    <svg class="mr-2" width="20" height="20" viewBox="0 0 20 20" preserveAspectRatio="xMinYMax">
                        <use xlink:href="#map-pin-line"></use>
                    </svg>
                    <span>{{ farm.city }}</span>
                </p>
                <p class="mt-3 text-gray-500" v-if="farm.content_text">{{ farm.content_text.slice(0, 120) }}...</p>
            </div>
            <div class="flex items-start justify-center" v-if="!isPopup">
                <svg @click="saveToFavorites()" class="mx-auto fill-current stroke-current text-black" width="25" height="25" viewBox="0 0 25 25" preserveAspectRatio="xMinYMax">
                    <use v-bind:xlink:href="'#favoriten'"></use>
                </svg>
            </div>
        </div>

        <div class="flex-1 bg-white pb-6 px-6 flex flex-col justify-around">
            <svg class="mr-2" width="20" height="20" viewBox="0 0 20 20" preserveAspectRatio="xMinYMax">
                <use :xlink:href="'#'+farm.reachability"></use>
            </svg>
        </div>
        <button class="absolute top-4 right-4 z-50" @click="closeTeaser()" v-if="isPopup">
            <svg width="30" height="30" viewBox="0 0 20 20" preserveAspectRatio="xMinYMax">
                <use xlink:href="#close"></use>
            </svg>
        </button>
    </div>
</template>

<script>
export default {
    props: {
        farm: Object,
        isPopup: Boolean
    },
    methods: {
        saveToFavorites () {
            localStorage.setItem('favorites', [item.id])
        },
        closeTeaser () {
            this.$emit('close');
        }
    }
}
</script>
