<template>
	<v-app>
		<AppBar></AppBar>
		<v-main>
			<router-view></router-view>
		</v-main>
	</v-app>
</template>

<script>
import AppBar from '@/components/AppBar.vue';
export default {
	components: { AppBar },
	data() {
		return {};
	},
	setup() {},
	created() {},
	mounted() {},
	unmounted() {},
	methods: {},
};
</script>
