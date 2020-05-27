<template>
    <div>
        <el-form :rules="rules" :model="loginForm" class="login-container" ref="loginForm">
            <h3 class="login_title">系统登录</h3>
            <el-form-item prop="username">
                <el-input type="text" v-model="loginForm.username" auto-complete="off" placeholder="请输入用户名"></el-input>
            </el-form-item>
            <el-form-item prop="password">
                <el-input type="text" v-model="loginForm.password" auto-complete="off" placeholder="请输入密码"></el-input>
            </el-form-item>
            <el-checkbox v-model="checked" class="login-remember"></el-checkbox>
            <el-button type="info" style="width:100%" @click="submitLogin">登录</el-button>

        </el-form>
    </div>
</template>

<script>
    export default {
        name: "Login",
        data(){
            return{
                rules:{
                    username: [{required: true, message: '请输入用户名', trigger: 'blur'}],
                    password: [{required: true, message: '请输入密码', trigger: 'blur'}]
                },
                loginForm: {
                    username: 'stephen',
                    password: '123'
                },
                checked:true
            }
        },
        methods:{
            submitLogin(){
                this.$refs.loginForm.validate((valid) => {
                    if (valid) {
                        alert('submit!');
                    } else {
                        this.$message.error("请输入所有字段")
                        return false;
                    }
                });
            }
        }
    }
</script>

<style>
    .login-container{
        border-radius: 15px;
        background-clip: padding-box;
        margin: 180px auto;
        width: 350px;
        padding: 35px 35px 15px 35px;
        background: #e3e2dc;
        border: 1px solid #eaeaea;
        box-shadow: 0 0 25px #cac6c6;
    }
    .login_title{
        margin: 0px auto 15px auto;
        text-align: center;
        color: #505458;
    }
    .login-remember{
        margin: auto auto 15px auto;
        text-align: left;
    }

</style>