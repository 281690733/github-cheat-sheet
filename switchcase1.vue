<template>
	
	<div id="aps" style="width: 100%;text-align: left;">
		<p>自动评价</p>
		<!-- 使用element的switch控件-->
		<span>
			<el-tooltip :content="'开启自动评价信誉分不会失'">
				<el-switch type="text" v-model="value" active-color="#13ce66" inactive-color="#D1EEEE" active-value="100" inactive-value="0" v-on:change="changes()">
				</el-switch>
			</el-tooltip>
		</span>
		
	</div>
</template>

<script>
	var nowvalue = '0';
	export default {
		data() {
			return {
				value: '100'
			}
		},
		methods: {
			//当switch改变时调用函数
			changes() {
				//当第一次改变时,判断当前的value值
				nowvalue = this.value;
				//当用户关闭时 nowvalue为0
				if (nowvalue == '0') {
					this.$confirm('亲, 是否继续关闭自动评价?', '提示', {
						confirmButtonText: '确定',
						cancelButtonText: '取消'
					}).then(() => {
						this.value = '0';
						this.$message({
							type: 'success',
							message: '已关闭自动评价!'
						});
					}).catch(() => {
						this.value = '100';
						this.$message({
							type: 'info',
							message: '已取消操作'
						});
					});
					nowvalue = this.value;
				} else {
					//当用户打开时 nowvalue为100
					nowvalue = this.value;
					//此时弹出登录界面 或者调用登录组件
					this.$alert('<div style="margin: 0 auto; text-align: center;" > <img src = "bad_evaluate.png" /><span> <big> 开启成功 </big></span> </div> <br ><br ><div > 软件到期将会自动关闭， 为有效避免店铺差评， 记得续费和开启 </div> <div><br/><input type = "checkbox" /> <span> 软件到期提醒我 </span> <br/><br/><input type = "text" placeholder = "填写手机号" style = "width: 200px; height: 20px;" /> &nbsp; &nbsp; <button style = "width: 100px; height: 26px;" > 发送验证码 </button> <br/><input type = "text" placeholder = "填写验证码" style = "width: 200px; height: 20px;"/> &nbsp; &nbsp; <button disabled = "true" style = "width: 100px; height: 26px;" > 开启提醒 </button> </div>', '', {
						dangerouslyUseHTMLString: true
					});
			}
		}
	}
	}
</script>

<style>
</style>
