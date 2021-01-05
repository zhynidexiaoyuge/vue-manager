<template>
	<div class="main_container">
		<div class="main_menus" style="width:200px">
			<el-menu unique-opened :default-active="$route.fullPath||oldActivePath" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose" :collapse="isCollapse">
				<el-menu-item :index="'/home_page'" @click="jump('/home_page')">
					<i :class="'fa fa-info-circle'"></i>
					<span slot="title">{{'首页'}}</span>
				</el-menu-item>
				<div v-for="(item,index) in firstMenu" :key="index">
					<el-submenu :index="item.url" v-if="item.children" @click="jump(item.url,item.openMode)">
						<template slot="title">
							<i :class="'fa '+item.icon"></i>
							<span slot="title">{{item.name}}</span>
						</template>
						<el-menu-item-group v-for="(s,j) in item.children" :key="j">
							<el-menu-item :index="s.url" @click="jump(s.url,s.openMode)" style="padding-left:50px;">{{s.name}}</el-menu-item>
						</el-menu-item-group>
					</el-submenu>
					<el-menu-item :index="item.url" @click="jump(item.url,item.openMode)" v-else>
						<i :class="'fa '+item.icon"></i>
						<span slot="title">{{item.name}}</span>
					</el-menu-item>
				</div>
			</el-menu>
		</div>
		<div class="main_content" style="margin-left:200px">
			<div class="header_container"></div>
			<div>
				<router-view class="main_view_content" />
			</div>

		</div>
	</div>
</template>
<script>
	export default {
		data() {
			return {
				isCollapse: false,
				oldActivePath: "",
			};
		},
		computed: {
			firstMenu() {
				return this.$store.state.menu.menuList;
			},
			secondMenu() {
				return (
					this.$store.state.menu.menuList.find(
						(m) => m.name === this.$route.matched[0].name
					) || {}
				).children;
			},
		},
		mounted() {
			[{ name: 1 }, { name: 2 }, { value: 1 }].find((item) => item.value === 1)
				?.name ?? "";
		},
		methods: {
			handleOpen(key, keyPath) {
				// console.log(key, keyPath);
			},
			handleClose(key, keyPath) {
				// console.log(key, keyPath);
			},
			jump(url, model) {
				this.oldActivePath = url;
				if (model) {
					window.open(url, "_blank");
				} else {
					if (url !== this.$router.history.current.fullPath) {
						this.$router.replace({ path: url });
					}
				}
			},
		},
	};
</script>
<style>
	.el-menu {
		border: 0;
		background: #1d1e23;
	}
	.el-menu--inline {
		background: #101117;
	}
</style>
<style scoped lang="scss">
	.main_container {
		width: 100%;
		height: 100%;
		// display: flex;
		.main_menus {
			float: left;
			height: 100%;
			background: #1d1e23;
			.fa {
				font-size: 14px;
				width: 30px;
				color: #fff;
			}
		}
		.main_content {
			width: 100%;
			height: 100%;
			// flex: 1;
			.main_view_content {
				width: 100%;
				height: 100%;
			}
		}
	}
</style>
