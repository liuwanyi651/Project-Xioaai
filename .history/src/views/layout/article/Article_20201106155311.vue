<template>
<div>
    <!--头部-->
    <div class="top"></div>
    <!--文章标题 及 文章摘要-->
    <div class="form">
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
            <el-form-item label="文章标题" prop="essay">
                <el-input v-model="ruleForm.essay"></el-input>
            </el-form-item>
        </el-form>
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
            <el-form-item label="文章摘要" prop="digest">
                <el-input v-model="ruleForm.digest"></el-input>
            </el-form-item>
        </el-form>
    </div>
    <!--作者及类目部分-->
    <div class="witer">
        <!--作者-->
        <div>
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
                <el-form-item label="作者" prop="name">
                    <el-input v-model="ruleForm.name"></el-input>
                </el-form-item>
            </el-form>
        </div>
        <!--类名-->
        <div>
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
                <el-form-item label="类名" prop="region">
                    <el-select v-model="ruleForm.region" placeholder="请选择">
                        <el-option v-for="item in option" :key="item.value" :label="item.label" :value="item.value">
                        </el-option>
                    </el-select>
                </el-form-item>
            </el-form>
        </div>
        <!--来源-->
        <div>
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
                <el-form-item label="来源" prop="region">
                    <el-select v-model="ruleForm.region" placeholder="请选择">
                        <el-option v-for="item in option" :key="item.value" :label="item.label" :value="item.value">
                        </el-option>
                    </el-select>
                </el-form-item>
            </el-form>
        </div>
        <!--重要性-->
        <div class="block" style="display: flex;">
            <!--<div class="demonstration" style="font-size: 14px;color:#606266;">重要性</div>-->
            <el-rate v-model="value1" style="line-height: 50px;"></el-rate>
        </div>
        <!--时间日期-->
        <div class="block">
            <el-date-picker v-model="value1" type="date" placeholder="选择日期">
            </el-date-picker>
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
                essay: '',
                digest: ''

            },
            rules: {
                essay: [{
                    required: true,
                    message: '请输入标题',
                    trigger: 'blur'
                }],
                digest: [{
                    required: true,
                    message: '请输入文章摘要',
                }],
            }
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
</style>
