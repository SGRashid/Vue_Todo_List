<template>
    <div class="loader d-flex">
        <img src="@/assets/packman.svg"
             class="m-auto"
        />
    </div>
</template>

<script>
    export default {
        name: "Loader"
    }
</script>

<style scoped>
    img {
        width: 100px;
    }
    .loader { height: 60vh; }
</style>