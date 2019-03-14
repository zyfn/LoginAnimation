<template>
<div class="Login">
    <div class="Login-bg"></div>
    <div class="Login-index">
        <div class="GoRegin" v-bind:class="{ComeLogin:isComeLogin,ComeRegin:isComeRegin}" v-if="!haveCount">
            <h1 style="padding-bottom:20%;color:#66CDAA">Regin</h1>
            <el-form :model="userRegin" status-icon  label-width="50px" ref="ruleForm2" class="demo-ruleForm">
                <el-form-item label="账号" prop="account">
                    <el-input v-model="userRegin.account" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="密码" prop="password">
                    <el-input type="password" v-model="userRegin.password" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="年龄" prop="age">
                    <el-input v-model.number="userRegin.age"></el-input>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="submitForm('userRegin')">注册</el-button>
                </el-form-item>
            </el-form>
        </div>
        <div class="GoLogin" v-bind:class="{ComeLogin:isComeLogin,ComeRegin:isComeRegin}" v-else>
            <h1 style="padding-bottom:20%;color:#66CDAA">Login</h1>
            <el-form :model="userRegin" status-icon :rules="rules2" label-width="50px" ref="ruleForm2" class="demo-ruleForm">
                <el-form-item label="账号" prop="account">
                    <el-input v-model="userRegin.account" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="密码" prop="password">
                    <el-input type="password" v-model="userRegin.password" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item>
                    <el-button type="primary" @click="submitForm('userRegin')">注册</el-button>
                </el-form-item>
            </el-form>
        </div>
        <div class="moveBg" v-bind:class="{moveBgRight:isCountNoExist,moveBgLeft:isCountExist}"></div>
        <div class="count-noexist" v-bind:class="{countNoExist:isCountNoExist,countNoExistMove:isCountExist}">
            <h1>没有账号?</h1>
            <el-button @click="ComeRegin()">点此注册</el-button>
        </div>
        <div class="count-exist" v-bind:class="{countExist:isCountExist,countExistMove:isCountNoExist}">
            <h1>已有账号?</h1>
            <el-button @click="ComeLogin()">点此登录</el-button>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            userRegin: {
                account: '',
                password: '',
                age: '',
            },
            isComeLogin: false,
            isCountExist: false,
            haveCount: false,
            isCountNoExist: false,
            isComeRegin: false,
        }
    },
    methods: {
        ComeLogin() {
            this.isComeLogin = true;
            this.isCountExist = true;
            this.isCountNoExist = false;
            this.isComeRegin = false;
            this.haveCount = true;
        },
        ComeRegin() {
            this.isCountNoExist = true;
            this.isComeRegin = true;
            this.isComeLogin = false;
            this.isCountExist = false;
            this.haveCount = false;
        }
    },
    mounted(){
        console.log(this.$attrs)
        console.log(this.$parent)
    }
}
</script>

<style>
.Login {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    height: 100vh;
}

.Login-bg {
    width: 100%;
    height: 100%;
    background: no-repeat url('../static/login.jpg');
    background-size: 100% 100%;
    filter: blur(5px);
    position: absolute;
    z-index: -1;
}

.Login-index {
    width: 60%;
    height: 500px;
    background-color: white;
    z-index: 0;
    margin-top: 10%;
    border-radius: 3%;
    position: relative;

}

.GoRegin {
    border: 1px solid gray;
    box-sizing: border-box;
    padding: 3% 10% 8% 8%;
    background-color: white;
    width: 52%;
    position: absolute;
    height:500px;
    box-shadow: 3px 3px 6px #888888;


}
.GoLogin{
    border: 1px solid gray;
    box-sizing: border-box;
    padding: 5% 10% 13% 8%;
    background-color: white;
    width: 52%;
    position: absolute;
    height:500px;
    box-shadow: 3px 3px 6px #888888;
}

.ComeLogin {
    animation: login 1s linear forwards;
}

.ComeRegin {
    animation: regin 1s linear forwards;
}

.countExist {
    animation: countExist 0.5s forwards;
}

.countExistMove {
    animation: countExistMove 1s linear forwards;
}

.countNoExist {
    animation: countNoExist 0.5s forwards;
}

.countNoExistMove {
    animation: countNoExistMove 1s linear forwards;
}

.count-noexist {
    margin-top: 10%;
    margin-left:15%;
    float: left;
}

.count-exist {
    margin-left: 55%;
    margin-top: 13%;
}

.moveBg {
    height: 500px;
    width: 50%;
    background: url('../static/3.jpg');
    background-size: 100% 100%;
    position: absolute;
    left: 50%;
    z-index: -1
}

.moveBgLeft {
    animation: moveBgLeft 1s linear forwards;
}

.moveBgRight {
    animation: moveBgRight 1s linear forwards;
}

@keyframes login {
    0% {
        left: 0%
    }

    25% {
        left: 25%
    }

    50% {
        left: 40%
    }

    75% {
        left: 53%
    }

    to {
        left: 50%;
    }

}

@keyframes regin {
    from {
        left: 50%;
    }

    25% {
        left: 30%;
    }

    50% {
        left: 15%
    }

    75% {
        left: -3%
    }

    to {
        left: 0%;
    }

}

@keyframes countExist {
    from {
         opacity: 1;
    }

    to {
          opacity: 0;
    }
}

@keyframes countExistMove {
    from {
      opacity: 0;
    }
    40%{
      opacity: 0;
    }
    70%{
      margin-left: 65%;
    }
    to {
        opacity: 1;
        margin-left: 55%;
    }
}
@keyframes countNoExist {
    from {
         opacity: 1;
    }

    to {
          opacity: 0;
    }
}

@keyframes countNoExistMove {
    from {
      opacity: 0;
    }
    40%{
      opacity: 0;
    }
    70%{
      margin-left: 10%;
    }
    to {
        opacity: 1;
        margin-left: 15%;
    }
}

@keyframes moveBgLeft {
    from {
        left: 50%;
         z-index: 2;
    }

    50% {
        left: 15%
    }

    75% {
        left: -3%
    }

    to {
        left: 0%;
        border-radius: 3%;
         z-index: -1;
    }
}

@keyframes moveBgRight {
    from {
        left: 0%;
        z-index: 2;
    }

    50% {
        left: 35%
    }

    75% {
        left: 53%
    }

    to {
        left:50%;
        border-radius: 3%;
        z-index: -1
    }
}
</style>
