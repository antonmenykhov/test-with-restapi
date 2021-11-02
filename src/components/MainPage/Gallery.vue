<template>
<gallery-wrapper fit-width="true" v-masonry transition-duration="0" item-selector=".gallery-item">
    <gallery-item v-masonry-tile v-for="post in posts" :key="post.id">
        <Title>{{post.title}}</Title>
        <description>{{post.body}}</description>
        <author>{{post.author.name}}</author>
    </gallery-item>
    
</gallery-wrapper>
</template>

<script>
import Author from '../General/Author.vue'

import Description from '../General/Description.vue'
import GalleryItem from '../General/GalleryItem.vue'
import GalleryWrapper from '../General/GalleryWrapper.vue'
import Title from '../General/Title.vue'
export default {
    components: { GalleryWrapper, GalleryItem, Title, Description, Author },
    props: {

        posts: Array,
    },

}
</script>

<style>

</style>
