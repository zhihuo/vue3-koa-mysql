<style lang="less" scoped>
.hearder{
    height: 50px;
    background-color: dimgray;
    color: #fff;
    overflow: hidden;
    line-height: 50px;
    padding: 10px 45px 10px 15px;
    .logo{
        float: left;
        font-size: 20px;
    }
    .userInfo{
        float:right;
        font-size: 14px;
    }
    .loginout{
        margin: 0 5px;
        a{
            color: #fff;
            text-decoration: none;
        }
    }
}
</style>
<template>
    <div class="hearder">
        <div class="logo">OPS系统</div>
        <div class="userInfo">
          <span class="username">{{info.name}}</span>
          <span class="loginout" @click="loginout">登出</span>
        </div>
    </div>
</template>
<script>
import { UsersList } from '../api/users'
import { LoginOut } from '../api/loginRegister'
export default {
	data(){
		return{
			info: []
		};
	},
	created(){
			this.init()
	},
	methods:{
		async init() {
			// const res = await this.$http.get('/info', {})
            const res = await UsersList({})
			// this.info = res.response
            this.info = res.data[0]
        },
        async loginout() {
            // const res = await this.$http.get('/loginout', {})
            const res = await LoginOut({})
            console.log('退出：', res)
            if (res.status === 200) {
                this.$router.push('login')
            }
		}
	}
}
</script>

