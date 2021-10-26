<template>
    <div>
        <p>
            用户名：<input type="text" name="username" v-model="username">
        </p>
        <p>
            密码：<input type="password" name="password" v-model="password">
        </p>
        <p>
            <button @click="doLogin">登录</button>
        </p>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                username: '',
                password: ''
            }
        },
        methods: {
            doLogin(){
                this.axios.post('/login', {
                    username: this.username,
                    password: this.password
                }).then(res => {
                    
                    console.log(res);



                    /* 
                        res.data = {
                            "code": "2200", // code 被称之为错误码
                            "data": {
                                state: "success"
                            }
                        } 
                    */
                    // 2200: 请求操作成功，但不代表业务逻辑成功
                    // 2500: 服务端业务失败
                    // 2400: 请求参数不合法
                    // 2401: 未登录或 token 过期
                    // let {code, data} = res.data;
                    // if(code == "2401"){
                    //     this.$router.push('/login')
                    // }else if(code == "2400"){
                    //     alert('参数不合法')
                    // }
                    /* if(data.state == 'success'){
                        this.$router.push('/')
                    }else{
                        alert('用户名或密码错误')
                    } */
                }).catch(error => {
                    console.log(error, '------');
                });
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>