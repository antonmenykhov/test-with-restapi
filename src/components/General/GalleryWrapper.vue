<template>
<div class="gallery-wrapper">
    <slot></slot>
</div>
</template>

<script>
export default {

}
</script>

<style lang="scss">
.gallery-wrapper {
    display: flex;
    justify-content: center;
    align-items: flex-start;
    width: 100%;
    flex-wrap: wrap;
    margin: 0 auto
}
</style>
