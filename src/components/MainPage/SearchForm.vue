<template>
<form class="searchForm">
    <button @click="submit" class="searchButton">
        <div class="icon"></div>
    </button>
    <text-input :setValue="setValue" :placeholder="search.placeholder" :name="search.name"></text-input>
</form>
</template>

<script>
import TextInput from '../Controls/TextInput.vue'
export default {
    props: {
        filterPosts: Function
    },
    components: { TextInput },
    data() {
        return {
            search: {
                name: 'search',
                placeholder: 'Enter Author Name',
                value: ''
            }
        }
    },
    methods: {
        setValue(data) {
            this.$set(this[data.name], 'value', data.value)
            console.log(this.search.value)
        },
        submit(e) {
            e.preventDefault();
            this.filterPosts(this.search.value)

        }
    },
}
</script>

<style lang="scss">
.searchForm {
    margin: 20px 0;
    display: flex;
    justify-content: center;
    align-items: stretch;

    button {
        width: 33px;
        margin-right: 5px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 4px;
        border: 1px solid rgba(0, 0, 0, 0.125);
        background: white;

        .icon {
            background: url('/img/search-solid.svg') no-repeat center center /contain;
            width: 60%;
            height: 60%;
        }
    }

    button:active {
        border-color: #80bdff;
        outline: 0;
        box-shadow: 0 0 0 0.2rem rgb(0 123 255 / 25%);
    }

    button:hover {
        border-color: #80bdff;
        outline: 0;
        box-shadow: 0 0 0 0.2rem rgb(0 123 255 / 25%);
    }

}
</style>
