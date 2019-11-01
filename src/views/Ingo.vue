<template>
	<div class="go">
		<h1>注册你的xx号</h1>
		用户名：<input type="text" v-model="user.name">
		<br>
		密码：<input type="password" v-model="user.pwd1">
		<br>
		重写密码：<input type="password" v-model="user.pwd2">
		<br>
		邮箱：<input type="email" v-model="user.email">
		<br>
		<button @click="gogo">注册你的xx</button>
	</div>
</template>


<script>
	export default{
		data(){
			return{
				user:{
					name:'',
					pwd1:'',
					pwd2:'',
					email:''
				}
			}
		},
		methods:{
			gogo(){
				if(this.user.name==""||this.user.pwd1==""||this.user.pwd2==""||this.user.email){
					alert("不能为空")
				}
				else if(this.user.pwd1!=this.user.pwd2){
					alert("密码不一致")
				}
				else{
					this.$http({
						url:'http://www.520mg.com/member/reg_new2.php',
						method:'post',
						withCredentials:true,
						data:`userid=${this.user.name}&userpwd=${this.user.pwd1}&email=${this.user.email}`
					}).then((res)=>{
						if(res.data.status==1){
							console.log(res.data)
							this.$router.push('/login')
						}
						else{
							
						}
					}).catch((err)=>{
						
					})
				}
				
			}
		}
	}
</script>

<style>
	.go{
		width: 200px;
		margin: 0 auto;
	}
</style>
