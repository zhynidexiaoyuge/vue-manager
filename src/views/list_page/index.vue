<template>
	<div class="bar_page_container">
		列表页面
		<div class="item" v-for="(item) in 100" :key="item">{{item}}</div>
	</div>
</template>

<script>
	// import HelloWorld from "./components/HelloWorld.vue";
	// import VUE_CONFIG from "VUE_CONFIG";
	import routers from "../../router/routers";
	export default {
		name: "list_page",
		data() {
			return {};
		},
		mounted() {
			console.log("组织好的路由数据如下所示");
			console.table(routers);
			// console.log(VUE_CONFIG);
		},
	};
</script>

<style scoped>
	.item {
		width: 100%;
		height: 40px;
		border-bottom: 1px solid #f0f;
	}
</style>
