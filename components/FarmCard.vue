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
            <div class="flex items-start justify-center">
                <svg @click.prevent="callFavorites()" class="mx-auto fill-current stroke-current text-black" width="25" height="25" viewBox="0 0 25 25" preserveAspectRatio="xMinYMax">
                    <use v-bind:xlink:href="svgId"></use>
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
    data() {
        return {
            favorite: false,
            favoritesList: []
            }
    },
    mounted() {
        this.loadLocalStorage()
    },
    computed: {
        svgId () {
            if (this.favorite) {
                return '#favoriten' + '-active'
            }
            return '#favoriten'
        }
    },
    methods: {
        loadLocalStorage() {
            if(localStorage.getItem('favorites')) {
                let storage = JSON.parse(localStorage.getItem('favorites'))
                this.favoritesList = storage
                if(storage.includes(this.farm.id)) {
                    this.favorite = true
                } else {
                    this.favorite = false
                }
                
            } else {
                let emptyList = JSON.stringify([])
                localStorage.setItem('favorites', emptyList)
                this.favoritesList = JSON.parse(emptyList)
            }
            
        },
        callFavorites() {
            // add to local stoarge
            if(!this.favorite) {
                let list = this.favoritesList
                list.push(this.farm.id)
                let stringfied = JSON.stringify(list)
                localStorage.setItem('favorites', stringfied)
                this.loadLocalStorage()
            } else {
                let list = this.favoritesList
                let index = list.indexOf(this.farm.id)
                list.splice(index,1)
                let stringfied = JSON.stringify(list)
                localStorage.setItem('favorites', stringfied)
                this.loadLocalStorage()
            }
        },
                closeTeaser () {
            this.$emit('close');
        }
    },
}
</script>
