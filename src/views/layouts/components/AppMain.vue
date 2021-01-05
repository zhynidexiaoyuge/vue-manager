<template>
	<div class="app-main">
		<transition name="fade" mode="out-in">
			<router-view></router-view>
		</transition>
	</div>
</template>

<script>
	export default {
		name: "AppMain",
	};
</script>
<style scoped lang="scss">
	.app-main {
		position: relative;
		height: 100%;
		width: 100%;
	}
</style>
