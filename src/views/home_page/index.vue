<template>
	<div class="bar_page_container">
		首页
	</div>
</template>

<script>
	// import HelloWorld from "./components/HelloWorld.vue";
	// import VUE_CONFIG from "VUE_CONFIG";
	import routers from "../../router/routers";
	export default {
		name: "home_page",
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
</style>
