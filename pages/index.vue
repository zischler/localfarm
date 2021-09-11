<template>
    <div>
        <svg-symbols />
        <vHeader />
        <teaser />
    </div>
</template>

<script>

import VHeader from '~/components/vHeader.vue'
import teaser from '~/components/teaser.vue'
import svgSymbols from '~/components/svgSymbols.vue'

export default {
    components: { VHeader, teaser, svgSymbols },
    methods: {
        async fetchMockApi () {
            await this.$axios.get(process.env.baseUrl)
                .then(response => console.log(response))
                .catch(error => console.error(error))
        }
    }
}
</script>
