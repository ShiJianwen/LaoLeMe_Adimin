<template>
	<div class="am-cf admin-main">
		<div class="admin-sidebar am-offcanvas" id="admin-offcanvas">
			<div class="am-offcanvas-bar admin-offcanvas-bar">
				<ul class="am-list admin-sidebar-list">
					<li>
						<a v-link="{path: '/'}">
							<span class="am-icon-home"></span>
							首页
						</a>
					</li>
					<li v-if="user">
						<a v-link="{path: '/user'}" >
							<span class="am-icon-table"></span>
							用户管理
						</a>
					</li>
					<li v-if="user">
						<a href="admin-form.html" v-link="{path: '/boss'}">
							<span class="am-icon-pencil-square-o"></span>
							店家管理
						</a>
					</li>
					<li v-if="user">
						<a href="#" v-link="{path: '/restaurant'}">
							<span class="am-icon-sign-out"></span>
							店铺管理
						</a>
					</li>
				</ul>

				<div class="am-panel am-panel-default admin-sidebar-panel">
					<div class="am-panel-bd">
						<p>
							<span class="am-icon-bookmark"></span>
							公告
						</p>
						<p>此系统略屌，请谨慎使用 —— 开发者注</p>
					</div>
				</div>
			</div>
		</div>
		<router-view></router-view>
	</div>

</template>
<script>
	module.exports = {
		data: function() {
			return {
				user: sessionStorage.user
			};
		},
		events: {
			'loggedin': function() {
				this.user = sessionStorage.user;
			},
			'loggedout': function() {
				this.user = null;
			}
		}
		
	};

</script>