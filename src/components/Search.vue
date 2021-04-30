<template>
    <div class="container">
        <div class="row">
            <div class="col-md-12">
                <form class="input-group" @submit.prevent>
                    <input type="text" class="form-control" v-model="query" v-on:keyup.enter="handleSearch">
                    <div class="input-group-append">
                        <button class="btn btn-outline-light" type="button" v-on:click="handleSearch">Submit</button>
                    </div>
                </form>
                
            </div>
        </div>
    </div>
</template>

<script>

export default {

    data() {
        return {
            query: '',
        }
    },
    methods: {
        handleSearch: function()
        {
            this.$emit('SearchRequested', this.query);
        }
    }
}
</script>

<style scoped>
span
{
    background: white;
}
button {
    line-height: 0.5;
}
</style>