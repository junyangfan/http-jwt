<template>
    <div>
        <i-input v-model="username" placeholder="请输入用户名..." style="width: 300px"></i-input>
        <i-button type="primary" @click="login()">登录</i-button>
    </div>
</template>

<script>
import {mapActions} from 'vuex' //使用vuex中的mapActions方法，不会的请参考我的文章vuex的使用方法
export default {
    data(){
        return{
            username:''  //定义一个用户名  
        }
    },
    methods:{
        ...mapActions(['toLogin']), //获取store.js文件中的actions中的toLogin方法
        login(){
            // console.log(this['toLogin'](this.username));
            //使用获取到的toLogin方法
            this['toLogin'](this.username).then(data=>{ //因为toLogin返回的是一个Promise，所以可以.then
                this.$router.push('/')  //登录成功，跳到首页面
            },err=>{
                this.$Message.error(err)
            })
        }
    }
}
</script>
