<template>
<div>
    <!-- 登录表单区域 -->
    <el-form label-width="0px">
        <!-- 用户名 -->
        <el-form-item>
            <el-input></el-input>
        </el-form-item>
        <!-- 密码 -->
        <el-form-item>
            <el-input></el-input>
        </el-form-item>
        <!-- 验证码 -->
        <el-form-item>
            <el-input></el-input>
        </el-form-item>
        <!-- 按钮区域 -->
        <el-form-item class="btns">
            <el-button type="primary">立即登录</el-button>
            <el-button type="primary">立即注册</el-button>
        </el-form-item>
    </el-form>

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
.btns {
    display: flex;
    justify-content: center;
}
</style>
