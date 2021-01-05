<template>
	<div class="main_container">
		<div class="site-menu" ref="siteMenuBox" style="width:64px">
			<site-menu ref="siteMenu"></site-menu>
		</div>
		<div class="main_content">
			<div class="header_container">
				<site-header @toggleMenu="toggleMenu"></site-header>
			</div>
			<div class="main_view_box">
				<router-view class="main_view_content" />
			</div>
		</div>
	</div>
</template>
<script>
	import siteMenu from "./components/siteMenu";
	import siteHeader from "./components/siteHeader";
	export default {
		components: { siteMenu, siteHeader },
		data() {
			return {};
		},
		computed: {},
		mounted() {},
		methods: {
			toggleMenu(flag) {
				this.$refs.siteMenu.isCollapse = flag;
				if (flag) {
					this.$refs.siteMenuBox.style.width = 64 + "px";
				} else {
					this.$refs.siteMenuBox.style.width = 200 + "px";
				}
			},
		},
	};
</script>
<style scoped lang="scss">
	.main_container {
		width: 100%;
		height: 100%;
		display: flex;
		.site-menu {
			float: left;
			height: 100%;
			background: var(--site-menu-bg);
			transition: all 0.3s ease-in-out;
		}
		.main_content {
			width: 100%;
			height: 100%;
			flex: auto;
			.header_container {
				width: 100%;
				height: 60px;
				position: fixed;
				z-index: 1;
				top: 0px;
				background: var(--site-menu-bg);
			}
			.main_view_box {
				position: relative;
				width: 100%;
				height: 100%;
				background: #f5f7f9;
				overflow-y: scroll;
				padding: 20px 12px 20px 20px;
				.main_view_content {
					width: 100%;
					min-height: calc(100% - 60px);
					margin-top: 60px;
					box-shadow: 0px 0px 6px #999;
					background: #fff;
				}
			}
		}
	}
</style>
