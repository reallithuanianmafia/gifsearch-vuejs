<template>
    <div class="container">
        <div class="row">
            <div class="col-md-12">
                <ul>
                    <li v-for="gif in gifs"><img :src="gif.images.fixed_height.url"></li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['gifs'],
}
</script>

<style>
li{
    list-style: none;
    float: left;
    margin: 20px;
}
</style>