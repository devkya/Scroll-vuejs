<template>
	<div>
		<v-app-bar app color="primary" dark>
			<v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
			<div class="d-flex align-center"></div>
		</v-app-bar>

		<v-navigation-drawer v-model="drawer" absolute temporary app>
			<v-list-item>
				<v-list-item-content>
					<v-list-item-title class="text-h6"> Application </v-list-item-title>
					<v-list-item-subtitle> subtext </v-list-item-subtitle>
				</v-list-item-content>
			</v-list-item>

			<v-divider></v-divider>

			<v-list dense nav>
				<v-list-item
					v-for="item in items"
					:key="item.title"
					:to="items.to"
					link
				>
					<v-list-item-icon>
						<v-icon>{{ item.icon }}</v-icon>
					</v-list-item-icon>

					<v-list-item-content>
						<v-list-item-title>{{ item.title }}</v-list-item-title>
					</v-list-item-content>
				</v-list-item>
			</v-list>
		</v-navigation-drawer>
	</div>
</template>
<script>
export default {
	components: {},
	data() {
		return {
			drawer: false,
			items: [
				{ title: 'Scroll Test', icon: 'mdi-view-dashboard', to: '/' },
				{ title: 'Photos', icon: 'mdi-image', to: '/test' },
				{ title: 'About', icon: 'mdi-help-box' },
			],
			right: null,
		};
	},
	setup() {},
	created() {},
	mounted() {},
	unmounted() {},
	methods: {},
};
</script>
