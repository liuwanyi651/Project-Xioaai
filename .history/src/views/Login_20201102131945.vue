<template>
<div>
    <div class="bg">
        <div class="box"></div>
    </div>
</div>
</template>

<script>
export default {
    name: '',
    props: {},
    data() {
        return {}
    },
    components: {},
    methods: {},
    mounted() {},
    computed: {},
    watch: {}
}
</script>

<style lang="scss" scoped>
.bg {
    width: 100%;
    height: 100%;
    background-image: url("./bg.jpg");
    position: absolute;
    background-size: cover;
    background-repeat: no-repeat;
}

.box {
    width: 500px;
    height: 500px;
    border: 1px solid #ccc;
}
</style>
