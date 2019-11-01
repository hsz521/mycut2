<template>
	<div class="logo">
		<h1>登录啦啦啦啦</h1>
		用户名：<input type="text" v-model="user.name">
		<br>
		密码：<input type="password" v-model="user.pwd">
		<br>
		<button @click="lol">登录</button>
	</div>
</template>

<script>
	export default{
		data(){
			return{
				user:{
					name:"zzy0371",
					pwd:"zzy0371"
				}
			}
		},
		methods:{
			lol(){
				this.$http({
					url:'http://www.520mg.com/member/index_login.php',
					method:'post',
					withCredentials:true,
					data:`fmdo=login&dopost=login&userid=${this.user.name}&pwd=${this.user.pwd}`
				}).then((res)=>{
					if(res.data.status==1){
						console.log("登录成功")
						this.$store.commit("setlog",true)
						console.log(this.$route)
						if(this.$route.query.redirect){
							this.$router.push(this.$route.query.redirect)
						}
					}
					else{
						console.log("登录失败")
					}
				})
			}
		}
	}
</script>

<style>
</style>

