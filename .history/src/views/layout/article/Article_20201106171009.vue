<template>
<div>
    <!--头部-->
    <div class="top"></div>
    <!--文章标题 及 文章摘要-->
    <div class="form">
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
            <el-form-item label="文章标题" prop="title">
                <el-input v-model="ruleForm.title"></el-input>
            </el-form-item>
            <el-form-item label="文章摘要" prop="digest">
                <el-input v-model="ruleForm.digest"></el-input>
            </el-form-item>
            <div class="box">
                <div>
                    <el-form-item label="作者" prop="author">
                        <el-input v-model="ruleForm.author"></el-input>
                    </el-form-item>
                </div>
                <!--类目-->
                <div>
                    <el-form-item label="类目" prop="category">
                        <el-select v-model="form.category" placeholder="请选择">
                            <el-option label="Vue" value="Vue"></el-option>
                            <el-option label="React" value="React"></el-option>
                            <el-option label="Node.js" value="Node.js"></el-option>
                            <el-option label="性能优化" value="性能优化"></el-option>
                            <el-option label="JavaScript" value="JavaScript"></el-option>
                            <el-option label="小程序" value="小程序"></el-option>
                            <el-option label="工具类" value="工具类"></el-option>
                            <el-option label="其他" value="其他"></el-option>
                        </el-select>
                    </el-form-item>
                </div>
                <!--来源-->
                <div>
                    <el-select v-model="ruleForm.region" placeholder="来源">
                        <el-option label="区域一" value="shanghai"></el-option>
                        <el-option label="区域二" value="beijing"></el-option>
                    </el-select>
                </div>
                <!--重要性-->
                <div>
                    <el-select v-model="ruleForm.region" placeholder="重要性">
                        <el-option label="区域一" value="shanghai"></el-option>
                        <el-option label="区域二" value="beijing"></el-option>
                    </el-select>
                </div>
                <!--时间-->
                <div class="block">
                    <span class="demonstration">时间</span>
                    <el-date-picker v-model="value1" type="datetime" placeholder="选择日期时间">
                    </el-date-picker>
                </div>
            </div>
        </el-form>
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
                title: '',
                digest: '',
                author: '',
                category: '',
            },
            rules: {
                title: [{
                    required: true,
                    message: '请输入标题',
                    trigger: 'blur'
                }],
                digest: [{
                    required: true,
                    message: '请输入文章摘要',
                    trigger: 'blur'
                }],
                author: [{
                    required: true,
                    message: '请输入作者名称',
                    trigger: 'blur'
                }],
                category: [{
                    required: true,
                    message: '请输入作者名称',
                    trigger: 'blur'
                }],
            },
            value1: ''

        }
    },
    components: {},
    methods: {
        submitForm(formName) {
            this.$refs[formName].validate((valid) => {
                if (valid) {
                    alert('submit!');
                } else {
                    console.log('error submit!!');
                    return false;
                }
            });
        },
        resetForm(formName) {
            this.$refs[formName].resetFields();
        }
    },
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

.box {
    display: flex;
}

.box>div {
    margin-left: 20px;
}
</style>
