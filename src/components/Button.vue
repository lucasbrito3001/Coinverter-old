<template>
    <button type="button" class="btn-primary">{{moeda}} para BRL</button>    
</template>

<script>
export default {
    props: ["moeda"]
}
</script>

<style scoped>
.btn-primary{
    border: none;
    margin: 10px;
    border-radius: 5px;
}
</style>