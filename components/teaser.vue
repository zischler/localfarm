<template>
    <div class="max-w-5xl w-full h-full mx-auto px-4">
        <a v-for="farm in farms" :key="farm.id" href="#" class="my-8 flex flex-col rounded-lg shadow-lg overflow-hidden border border-gray-200">
            <div class="flex-shrink-0">
                <img class="h-48 w-full object-cover" src="https://images.unsplash.com/photo-1500382017468-9049fed747ef?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=3589&q=80" alt="">
            </div>
            <div class="flex-1 bg-white p-6 flex flex-col justify-between">
                <div class="flex-1">
                    <h1 class="text-xl mb-2 font-semibold text-gray-900">{{ farm.title }}</h1>
                    <p class="text-sm font-medium text-gray-500 flex mb-4">
                        <svg class="mr-2" width="20" height="20" viewBox="0 0 20 20" preserveAspectRatio="xMinYMax">
                            <use xlink:href="#map-pin-line"></use>
                        </svg>
                        <span>{{ farm.city }}</span>
                    </p>
                    <p class="mt-3 text-base text-gray-500">{{ farm.info_text.slice(0, 120) }}...</p>
                </div>
            </div>

            <div class="flex-1 bg-white pb-6 px-6 flex flex-col justify-around">
                <svg class="mr-2" width="20" height="20" viewBox="0 0 20 20" preserveAspectRatio="xMinYMax">
                    <use xlink:href="#map-pin-line"></use>
                </svg>
            </div>
        </a>
    </div>
</template>

<script>
export default {
    props: {
        farms: Object
    }
}
</script>
