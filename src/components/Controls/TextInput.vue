<template>
  <input :name="name" v-model="currentValue" :placeholder="placeholder" type="text">
</template>

<script>

export default {
props:{
    placeholder: String,
    setValue: Function,
    name: String
},
data() {
    return {
        currentValue: ''
    }
},
watch: {
    currentValue: function() {
        this.setValue({
            name: this.name,
            value: this.currentValue
        })
    }
}
}
</script>

<style>
input{
    width: 250px;
    padding: 6px 12px;
    border-radius: 4px;
    border: 1px solid rgba(0, 0, 0, 0.125);
}
input:focus{
    border-color: #80bdff;
    outline: 0;
    box-shadow: 0 0 0 0.2rem rgb(0 123 255 / 25%);
}
</style>