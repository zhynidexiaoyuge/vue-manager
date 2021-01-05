<template>
	<div id="app">
		<router-view class="pf" />
	</div>
</template>

<script>
	import { mapState, mapMutations } from "vuex";
	import store from "./store";
	export default {
		name: "App",
		components: {},
		computed: mapState(["theme", "isLogin"]),
		created() {
			this.setTheme(this.theme.name);
		},
		methods: {
			...mapMutations("theme", ["setTheme"]),
		},
	};
</script>

<style scoped lang="scss">
	#app {
		width: 100%;
		height: 100%;
		.pf {
			width: 100%;
			height: 100%;
		}
	}
</style>
