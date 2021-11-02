<template>
<p class="description">
    <slot></slot>
</p>
</template>

<script>
export default {

}
</script>

<style>
.description {
    color: rgb(167, 168, 169);
    font-size: 16px;
    text-align: left;
}

.description::first-letter {
    text-transform: uppercase
}
</style>
