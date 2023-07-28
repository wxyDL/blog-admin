<template>
    <div class="user-box">
        <div class="looginForm">
            <div class="looginForm-left">
                <div class="pic"></div>
            </div>
            <div class="looginForm-right">
                <h3 class="form-title">Welcome Back</h3>
                <div class="form-box">
                    <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="80px" class="demo-ruleForm">
                        <el-form-item label="用户名：" prop="userName">
                            <el-input v-model="ruleForm.userName">
                                <i slot="prefix" class="el-icon-user"></i>
                            </el-input>
                        </el-form-item>
                        <el-form-item label="密  码：" prop="password">
                            <el-input type="password" v-model="ruleForm.password">
                                <i slot="prefix" class="el-icon-lock"></i>
                            </el-input>
                        </el-form-item>
                    </el-form>
                    <el-button class="form-bth" type="primary" @click="loginFn">登录</el-button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {},
    components: {},
    computed: {},
    created() {
    },
    data() {
        return {
            ruleForm: {},
            rules: {
                userName: [
                    { required: true, message: '请输入用户名', trigger: 'blur' },
                    { min: 5, max: 10, message: '长度在 5 到 10 个字符', trigger: 'blur' }
                ],
                password: [
                    { required: true, message: '请输入密码', trigger: 'blur' },
                    { min: 6, max: 12, message: '长度在 6 到 12 个字符', trigger: 'blur' }
                ]
            }
        }
    },
    methods: {
        loginFn () {
            this.$refs.ruleForm.validate(vali => {
                if (!vali) {
                    this.$message.error('请完善信息!')
                    return
                } else {
                    this.$message.success('登录成功')
                    this.$router.push('/home')
                }
            })
        }
    }
}
</script>

<style lang="scss" scoped>
.user-box{
    width: 100%;
    height: 100%;
    background: url("@/assets/image/loginBj.jpg") no-repeat center;
    background-size: cover;
    position: relative;
    .looginForm{
        display: flex;
        height: 450px;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        .looginForm-left{
            position: relative;
            width: 180px;
            height: 100%;
            background: rgba(117,67,50,.7);
            .pic{
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                width: 130px;
                height: 130px;
                border-radius: 50%;
                background: url("@/assets/image/用户.svg");
            }
        }
        .looginForm-right{
            text-align: center;
            width: 400px;
            height: 100%;
            background: rgba(117,67,50,.3);
            .form-title{
                margin-top: 50px;
                font-size: 30px;
                font-weight: normal;
                color: #ffffff;
                opacity: .8;
            }
            .form-box{
                height: calc(100% - 150px);
                margin-top: 50px;
                .el-form{
                    width: 90%;
                    height: calc(100% - 150px);
                    margin-left: 13px;
                    .el-form-item{
                        ::v-deep .el-form-item__label{
                            color: #ffffff;
                        }
                    }
                }
                .form-bth{
                    width: 90%;
                    margin: -10px 0 0 -10px;
                    background: rgb(0,137,123);
                    border: none
                }
            }
        }
    }
}
</style>