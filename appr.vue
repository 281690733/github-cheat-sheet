<template>
	<div id="appr">
		<h3 style="text-align: left;">设置规则</h3>
		<div style="text-align: left;" >
			<!--好评模块-->
			<div style="text-align: right; width: 150px; position: absolute;">选择评价类型:</div>
			<div style="text-align: left; width: 850px; position: absolute; margin-left: 180px;">
				<el-radio v-model="radio" label="1"><img src="../../public/img/good_evaluate.png"/>(建议使用)</el-radio>
				<el-radio v-model="radio" label="2"><img src="../../public/img/neutral_evaluate.jpg"/>中评</el-radio>
				<el-radio v-model="radio" label="3"><img src="../../public/img/bad_evaluate.png"/>差评</el-radio>
			</div>
			<br />
			<br />
			<br />
			<!--设置评价规则-->
			<div style="text-align: right; width: 150px; position: absolute;">设置评价规则:</div>
			<div style="text-align: left; width: 850px; position: absolute; margin-left: 180px;">
				<el-radio v-model="radio1" label="1">交易后立即评价</el-radio>
				<br />
				<br />
				<el-radio v-model="radio1" label="2">交易后延迟7天给予评价 <el-checkbox v-model="checked1" v-bind:checked="checked()">买家已评，卖家立即回评</el-checkbox></el-radio>
				<br />
				<br />
				<el-radio v-model="radio1" label="3">抢评，在评价有效期中的最后评价<el-checkbox v-model="checked2" v-bind:checked="checked()">买家已评，卖家立即回评</el-checkbox></el-radio>
				<br />
				<br />
				<el-radio v-model="radio1" label="4">买家未评，卖家不回评，买家已评，卖家立即回评</el-radio>
			</div>
			<br />
			<br />
			<br />
			<br />
			<br />
			<br />
			<br />
			<br />
			<br />
			<!--设置回评过滤条件-->
			<div style="text-align: right; width: 150px; position: absolute;">设置回评过滤条件:</div>
			<div style="text-align: left; width: 850px; position: absolute; margin-left: 180px;">
				<el-checkbox v-model="checked3" v-bind:checked="checked2">给过中差评的用户自动加入黑名单&nbsp;<el-link type="primary">查看黑名单</el-link></el-checkbox>
			</div>
			<br />
			<br />
			<br />
			<div style="text-align: right; width: 150px; position: absolute;">黑名单评价规则:</div>
			<div style="text-align: left; width: 850px; position: absolute; margin-left: 180px;">
				<el-radio v-model="radio2" label="1">黑名单的用户不自动评价</el-radio>
				<el-radio v-model="radio2" label="2">黑名单中的用户自动回复差评</el-radio>
			</div>
			<br />
			<br />
			<br />
			<!--设置回评内容:-->
			<div style="text-align: right; width: 150px; position: absolute;">设置回评内容:</div>
			<div style="text-align: left; width: 850px; position: absolute; margin-left: 180px;">
				<label id="xuhua">(最多十条，多条将随机评价)</label>
				&nbsp;&nbsp;
				<el-link type="primary">系统模板</el-link>
				&nbsp;&nbsp;
				<el-link type="primary">自定义模板</el-link>
			</div>
			<br>
			<br>
			<!-- 分批显示模块-->
			<div style="text-align: left; width: 850px; position: absolute; margin-left: 180px;">
				<div id="asp">
					<div>
						<el-table :data="tableData" height="120px" style="width: 25%;border: #ffffff;border-bottom: #ffffff;position: absolute;margin-left: 0%;">
							<el-table-column prop="address">
							</el-table-column>
						</el-table>
					</div>
					<div>
						<el-table :data="tableData" height="120px" style="width: 25%;border: #ffffff;border-bottom: #ffffff;position: absolute;margin-left: 30%;">
							<el-table-column prop="address">
							</el-table-column>
						</el-table>
					</div>
					<div>
						<el-table :data="tableData" height="120px" style="width: 25%;border: #ffffff;border-bottom: #ffffff;position: absolute;margin-left: 60%;">
							<el-table-column prop="address">
							</el-table-column>
						</el-table>
					</div>
				</div>
				<a type="primary1" style="position: absolute; margin-top: 130px; cursor: pointer;color: skyblue;" v-on:click="getmore()">更多^</a>
				<el-button type="primary" style="margin-top: 200px;">保存并开启</el-button>
			</div>
			
		</div>
		
	</div>
</template>

<script>
	export default {
    data () {
      return {
        radio: '1',
		radio1: '1',
		radio2: '1',
		checked1: false,
		checked2:false,
		checked3:false,
		tableData: [{
			address: '上海市普陀区金沙江路 1518 弄sssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssssss'
		}]
      };
    },
	methods: {
		//当项目checkbox被选择时，事件绑定
		checked:function(){
			if(this.checked1 == true){
				this.radio1 = '2';
				this.checked2 == false;
			}
			else if(this.checked2 == true){
				this.checked1 == false;
				this.radio1 = '3';
			}
		},
		getmore(){
			var child = "";
			child += '<div>';
			child += '<el-table :data="tableData" height="120px" style="width: 25%;border: #ffffff;border-bottom: #ffffff;position: absolute;margin-top: 150px;margin-left: 150px;">';
			child += '<el-table-column prop="address">';
			child += '</el-table-column>';
			child += '</el-table>';
			child += '<div>';
			document.getElementById("#asp").appendChild(child);
		}
	}
	
  }
</script>

<style>
	#xuhua{
		opacity: 0.5;
	}
</style>
