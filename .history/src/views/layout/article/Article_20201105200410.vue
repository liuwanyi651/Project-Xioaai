<template>
<div>
    <div class="top"></div>
    <div class="form">
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
            <el-form-item label="文章标题" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
            </el-form-item>
        </el-form>
    </div>
    <div class="form">
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
            <el-form-item label="文章摘要" prop="name">
                <el-input v-model="ruleForm.name"></el-input>
            </el-form-item>
        </el-form>
    </div>
    <div class="witer">
        <div>
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
                <el-form-item label="作者" prop="name">
                    <el-input v-model="ruleForm.name"></el-input>
                </el-form-item>
            </el-form>
        </div>
    </div>
</div>
</template>

<script>
export default {
    name: '',
    props: {},
    data() {
        return {
            ruleForm: {
                name: ''

            },
            rules: {
                name: [{
                    required: true,
                    message: '请输入活动名称',
                    trigger: 'blur'
                }]
            }
        }
    },
    components: {},
    methods: {},
    mounted() {},
    computed: {},
    watch: {}
}
</script>

<style lang="scss" scoped>
.top {
    width: 1357px;
    height: 40px;
    background: rgb(13, 134, 13);
}

.form {
    margin-top: 20px;
}

.witer {
    display: flex;
}
</style>
