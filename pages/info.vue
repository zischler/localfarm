<template>
    <div class="max-w-5xl w-full h-full mx-auto px-4 pb-12">
        <div class="my-4">
            <h1 class="text-2xl">Weitere Informationen</h1>
            <p class="mt-3">
                Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam 
                nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam 
                erat, sed diam voluptua. At vero eos et accusam.
            </p>
        </div>
        <div class="link-list mt-8">
            <a href="#" class="py-2 pl-6 pr-3 border border-black rounded-full my-4 flex w-full justify-between">
                <span>AGB</span>
                <svg class="fill-current stroke-current text-black" width="25" height="25" viewBox="0 0 25 25" preserveAspectRatio="xMinYMax">
                    <use v-bind:xlink:href="'#arrow-right'"></use>
                </svg>
            </a>

            <a href="#" class="py-2 pl-6 pr-3 border border-black rounded-full my-4 flex w-full justify-between">
                <span>Kontakt</span>
                <svg class="fill-current stroke-current text-black" width="25" height="25" viewBox="0 0 25 25" preserveAspectRatio="xMinYMax">
                    <use v-bind:xlink:href="'#arrow-right'"></use>
                </svg>
            </a>

            <a href="#" class="py-2 pl-6 pr-3 border border-black rounded-full my-4 flex w-full justify-between">
                <span>Impressum</span>
                <svg class="fill-current stroke-current text-black" width="25" height="25" viewBox="0 0 25 25" preserveAspectRatio="xMinYMax">
                    <use v-bind:xlink:href="'#arrow-right'"></use>
                </svg>
            </a>

            <a href="#" class="py-2 pl-6 pr-3 border border-black rounded-full my-4 flex w-full justify-between">
                <span>Icon Legende</span>
                <svg class="fill-current stroke-current text-black" width="25" height="25" viewBox="0 0 25 25" preserveAspectRatio="xMinYMax">
                    <use v-bind:xlink:href="'#arrow-right'"></use>
                </svg>
            </a>
        </div>
    </div>
</template>

<script>
export default {

}
</script>