<template>
<div>
    <div class="tubiao">
        <ve-radar :data="chartData"></ve-radar>
    </div>
    <div class="tubiao"></div>
    <div class="tubiao"></div>
</div>
</template>

<script>
import axios from "axios";
export default {
    name: "",
    props: {},
    data() {
        return {
            chartData: {
                columns: [], //键
                rows: [], //键对应的数组
            },
        };
    },
    components: {},
    methods: {
        radarmap() {
            axios
                .get("/api/radarChat")
                .then((res) => {
                    let map = res.data;
                    console.log(map);

                })
                .catch((err) => {
                    console.log(err);
                });
        },
    },
    mounted() {
        this.radarmap()
    },
    computed: {},
    watch: {},
};
</script>

<style lang="scss" scoped>
.tubiao {
    width: 33.2%;
    background: white;
}
</style>
