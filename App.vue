<template>
  <div id="app">
  <el-tabs :tab-position="tabPosition" style="height: 1500px;">
    <el-tab-pane label="自动评价" style="height:1500px;">
			<switchcase1></switchcase1>
			<appr></appr>
		</el-tab-pane>
    <el-tab-pane label="批量评价">批量评价</el-tab-pane>
    <el-tab-pane label="角色管理">角色管理</el-tab-pane>
    <el-tab-pane label="定时任务补偿">定时任务补偿</el-tab-pane>
  </el-tabs>
  </div>
</template>

<script>
import appr from './components/appr.vue'
import switchcase1 from './components/switchcase1.vue'
export default {
  name: 'app',
  components: {
    appr,
		switchcase1
  },
	data() {
    return {
      tabPosition: 'left'
    };
	}
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
