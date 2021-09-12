<template>
    <a :href="to" class="w-full flex justify-between link-bg px-4 py-2 max-w-xs relative my-2">
        <span>{{ text }}</span>
        <svg
            width="30"
            height="30"
            viewBox="0 0 20 20"
            preserveAspectRatio="xMinYMax"
            class="absolute top-1/2 transform -translate-y-1/2 right-2"
        >
            <use xlink:href="#arrow-right"></use>
        </svg>
    </a>
</template>

<script>
export default {
    props: {
        to: String,
        text: String
    }
}
</script>

<style scoped>
.link-bg {
    background-image: url(../static/dropdown.svg);
    background-repeat: no-repeat;
    background-size: cover;
}
</style>