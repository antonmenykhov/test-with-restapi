<template>
<div class="gallery-item">
    <slot></slot>
</div>
</template>

<script>
export default {

}
</script>

<style>
.gallery-item {
    width: 300px;
    margin: 5px 10px;
    padding: 20px;
    background: white;
    border: 1px solid rgba(0, 0, 0, 0.125);
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}
@media (max-width: 370px) {
    .gallery-item{
        width: 200px;
    }
}
</style>
