<template>
<div class="all">
    <div class="zhichi">支持拖拽</div>
    <div class="Element">Element UI自带上传组件</div>
    <div class="pc">
        <el-upload class="upload-demo" drag action="/api/upload" multiple>
            <i class="el-icon-upload"></i>
            <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
            <div class="el-upload__tip" slot="tip">只能上传jpg/png文件，且不超过500kb</div>
        </el-upload>
    </div>
    <div class="zhichi">支持裁剪</div>
    <div class="Element">Element UI自带上传组件</div>
    <div class="btn">
        <el-button type="primary" @click="toggleShow">上传图片</el-button>
        <my-upload @crop-success="cropSuccess" @crop-upload-success="cropUploadSuccess" @crop-upload-fail="cropUploadFail" v-model="show" :width="200" :height="200" img-format="png" :size="size" langType=‘zh‘ :noRotate=‘false‘ field="Avatar1" url="https://httpbin.org/post"></my-upload>
        <img :src="imgDataUrl">
    </div>
</div>
</template>

<script>
import axios from 'axios'
import 'babel-polyfill';
import myUpload from 'vue-image-crop-upload';
// 引用第二种上传方式组件
import Pictureup from "../../../components/pictureUp/Pictureup"
export default {
    name: '',
    props: {},
    data() {
        return {

        }
    },
    components: {
        Pictureup
    },
    methods: {

    },
    mounted() {

    },
    computed: {},
    watch: {}
}
</script>

<style lang="scss" scoped>
.all {
    height: 100vh;
    background: white;
}

.zhichi {
    margin-top: 30px;
    font-size: 20px;
    font-weight: bold;
    margin-left: 30px;
    padding: 20px 0;
}

.Element {
    width: 95%;
    background: rgb(231, 233, 236);
    margin-left: 30px;
    padding: 20px 5px;
}

.pc {
    margin-left: 30px;
    margin-top: 20px;
}

.btn {
    margin-left: 30px;
    margin-top: 20px;
}
</style>
