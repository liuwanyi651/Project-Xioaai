<template>
<div class="bg">
    <div class="box">
        <div class="line">
            <!-- 登录表单区域 -->

            <el-form :model="loginForm" :rules="loginFormRules" label-width="0px" class="login-form" ref="formName">
                <!-- 用户名 -->
                <el-form-item prop="username">
                    <!-- 首部图标 -->
                    <el-input v-model="loginForm.username" prefix-icon="iconfont icon-yonghuming" placeholder="请输入用户名"></el-input>
                </el-form-item>
                <!-- 密码 -->
                <el-form-item prop="password">
                    <el-input v-model="loginForm.password" prefix-icon="iconfont icon-password" type="password" placeholder="请输入密码"></el-input>
                </el-form-item>
                <!-- 验证码 -->
                <el-form-item prop="yz">
                    <el-input style="width:220px;" placeholder="请输入验证码" v-model="loginForm.yz"></el-input>
                    <el-input style="width:220px;" v-html="yzm"></el-input>
                </el-form-item>
                <!-- 按钮区域 -->
                <el-form-item class="btns">
                    <el-button type="primary" @click="denglu">立即登录</el-button>
                    <el-button type="primary">立即注册</el-button>
                </el-form-item>
            </el-form>
        </div>
    </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
    name: '',
    props: {},
    data() {
        return {
            //登录表单的数据绑定对象
            loginForm: {
                username: '',
                password: '',
                yz: ''
            },
            //这是表单的验证规则对象
            loginFormRules: {
                // 验证用户名是否合法
                username: [{
                        required: true,
                        message: '用户名不能为空',
                        trigger: 'blur'
                    },
                    {
                        min: 2,
                        max: 8,
                        message: '用户名在2-8位之间',
                        trigger: 'blur'
                    }
                ],
                // 验证密码是否合法
                password: [{
                        required: true,
                        message: "密码不能为空",
                        trigger: "blur"
                    },
                    {
                        min: 1,
                        max: 15,
                        message: "密码在6~15位",
                        trigger: "blur"
                    }

                ],
                yz: [{
                    required: true,
                    message: "验证码不能为空",
                    trigger: "blur"
                }]
            },
            yzm: {} //验证码
        }
    },
    components: {},
    methods: {
        getData() {
            axios.get('/api/captcha').then((res => {
                this.yzm = res.data;
            })).catch((err => {
                console.log(err);
            }))
        },
        denglu() {
            this.$refs.formName.validate((valid) => {
                console.log(valid);
                if (valid) {
                    axios
                        .post("/api/user/login", {
                            username: this.loginForm.username,
                            password: this.loginForm.password,
                            code: this.loginForm.yz,
                        })
                        .then((res) => {
                            console.log(res);
                            if (res.data.code === 200) {
                                this.$message.success(res.data.message)
                                this.$router.push("/")

                            } else if (res.data.code === 1) {
                                this.$message.warning(res.data.message)
                                this.loginForm.username = ""
                                this.loginForm.password = ""
                                this.loginForm.checkPass = ""
                            }
                            console.log(res.data)
                        })
                        .catch((err) => {
                            console.log(err)
                        });
                } else {
                    this.$message.error("错误")
                    return false;
                }
            })

        }
    },
    mounted() {
        this.getData()
    },
    computed: {},
    watch: {}
}
</script>

<style lang="scss" scoped>
.bg {
    width: 100%;
    height: 100%;
    background-size: cover;
    position: absolute;
    background: rgb(191, 232, 245);
}

.box {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
}

.line {
    width: 500px;
    height: 300px;
    background: white;
    border: 1px solid #ccc;
}

.login-form {
    margin-top: 40px;
    padding: 0 20px;
    box-sizing: border-box;
}

.btns {
    display: flex;
    justify-content: center;
}
</style>
