<template>
<div id="app">
    <container>
        <search-form :filterPosts="filterPosts"></search-form>
        <gallery :posts="filteredPosts" />
        <p v-if="filteredPosts.length === 0" class="noPosts">No posts. Change your query, please</p>
    </container>
</div>
</template>

<script>
import axios from 'axios'
import constants from './constants'
import Gallery from './components/MainPage/Gallery.vue'
import Container from './components/General/Container.vue'
import SearchForm from './components/MainPage/SearchForm.vue'

export default {
    name: 'App',
    components: {
        Gallery,
        Container,
        SearchForm

    },
    data() {
        return {
            posts: [],
            filteredPosts: [],
            users: []
        }
    },
    created() {

        this.getUsers()
    },
    methods: {

        getPosts() {
            axios.get(constants.posts).then(
                response => {
                    this.posts = response.data;
                    this.connectPostsUsers()
                    this.filteredPosts = this.posts.slice()
                }
            )
        },
        getUsers() {
            axios.get(constants.users).then(
                response => {
                    this.users = response.data
                    this.getPosts()
                }
            )
        },
        connectPostsUsers() {
            this.posts.forEach(element => {
                element.author = this.users.find(user => user.id === element.userId)
            });
        },
        filterPosts(name) {
            if (name == "") {
                this.filteredPosts = this.posts.slice()
            } else {
              this.filteredPosts = []
                this.posts.forEach(elem =>{
                  if (elem.author.name.toLowerCase().indexOf(name.toLowerCase()) != -1){
                    this.filteredPosts.push(elem)
                  } 
                })
            }
        },
        getAuthor(id) {
            let userName = this.users.find(user => user.id == id).name
            return userName
        }
    },
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;700&display=swap');

#app {
    background: rgb(234,239,244);
    display: flex;
    align-items: flex-start;
    justify-content: center;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2C2738;
    min-height: 100vh;

}

* {
    font-family: IBM Plex Sans, sans-serif;
    margin: 0;
    padding: 0;
    text-decoration: none;
}
</style>
