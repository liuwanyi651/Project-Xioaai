<template>
<div>
    <ve-pie :data="chartData"></ve-pie>
</div>
</template>

<script>
import axios from 'axios'
//引入lodash
import groupBy from 'lodash/groupBy'
export default {
    name: '',
    props: {},
    data() {
        return {
            arr: [],

        }
    },
    components: {},
    methods: {
        getData() {
            axios.get('/api/article/allArticle ').then(res => {
                this.arr = res.data.data
                console.log(res.data.data)
            }).catch(err => {
                console.log(err)
            })
        }
    },
    mounted() {
        this.getData()
    },
    computed: {

    },
    watch: {}
}
</script>

<style lang='scss' scoped>

</style>
