<script>
export default {
    name: "Loader",




}
</script>


<template>
    <div class="loader d-flex justify-content-center align-items-center">
        <div class="spinner-grow text-dark spinner" role="status">
            <span class="visually-hidden">Loading...</span>
        </div>
    </div>
</template>


<style lang="scss" scoped>
.loader {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background-color: rgba(255, 255, 255, 0.94);
    z-index: 999;
    height: 100vh;

    .spinner {
        height: 200px;
        width: 200px;
    }

}
</style>