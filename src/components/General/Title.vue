<template>
  <h3><slot></slot></h3>
</template>

<script>
export default {

}
</script>

<style>
h3{
    font-size: 18px;
    color: rgb(78,151,231);
    margin-bottom: 20px;
    text-align: left;
}
h3::first-letter{
    text-transform: uppercase;
}
</style>