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
        </el-form>
        <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
            <el-form-item label="文章摘要" prop="digest">
                <el-input v-model="ruleForm.digest "></el-input>
            </el-form-item>
        </el-form>
    </div>
    <!--作者及类目部分-->
    <div class="witer">
        <!--作者-->
        <div>
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
                <el-form-item label="作者" prop="author">
                    <el-input v-model="ruleForm.author"></el-input>
                </el-form-item>
            </el-form>
        </div>
        <!--类名-->
        <div>
            <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px" class="demo-ruleForm">
                <el-form-item label="类名" prop="region">
                    <el-select v-model="ruleForm.taxon" placeholder="请选择">
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
                    <el-select v-model="ruleForm.source" placeholder="请选择">
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
                name: '',
                region: ''

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
                }]
            },
            options: [{
                value: '选项1',
                label: '财经'
            }, {
                value: '选项2',
                label: '新闻'
            }, {
                value: '选项3',
                label: '政治'
            }, {
                value: '选项4',
                label: '体育'
            }, {
                value: '选项5',
                label: '股票'
            }],
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
