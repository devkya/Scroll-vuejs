<template>
	<div>
		<!-- tbody scrollHeight 테스트 -->
		<v-row justify="center" align="center" class="pa-5">
			<v-subheader>Offset Top5</v-subheader>
			{{ offsetTop5 }}
			<v-btn @click="ScrollHeight" class="ma-5">TEST</v-btn>
		</v-row>
		<v-data-table
			id="scrollHeight1"
			:headers="headers"
			:items="desserts"
			:disable-pagination="true"
		>
			<template v-slot:body="{ items }">
				<tbody id="scrollHeight-tbody1" v-scroll.self="ScrollHeight">
					<tr v-for="(item, idx) in items" :key="idx">
						<td>{{ item.name }}</td>
						<td>{{ item.calories }}</td>
						<td>{{ item.fat }}</td>
						<td>{{ item.carbs }}</td>
						<td>{{ item.protein }}</td>
						<td>{{ item.iron }}</td>
					</tr>
				</tbody></template
			>
		</v-data-table>

		<v-data-table
			id="scrollHeight2"
			:headers="headers"
			:items="desserts"
			:disable-pagination="true"
		>
			<template v-slot:body="{ items }">
				<tbody id="scrollHeight-tbody2" v-scroll.self="ScrollHeight">
					<tr v-for="(item, idx) in items" :key="idx">
						<td>{{ item.name }}</td>
						<td>{{ item.calories }}</td>
						<td>{{ item.fat }}</td>
						<td>{{ item.carbs }}</td>
						<td>{{ item.protein }}</td>
						<td>{{ item.iron }}</td>
					</tr>
				</tbody></template
			>
		</v-data-table>
	</div>
</template>
<script>
export default {
	components: {},
	name: 'ScrollTable',
	data() {
		return {
			target: null,
			offsetTop5: 0,
			headers: [
				{
					text: 'Dessert (100g serving)',
					align: 'start',
					sortable: false,
					value: 'name',
				},
				{ text: 'Calories', value: 'calories' },
				{ text: 'Fat (g)', value: 'fat' },
				{ text: 'Carbs (g)', value: 'carbs' },
				{ text: 'Protein (g)', value: 'protein' },
				{ text: 'Iron (%)', value: 'iron' },
			],
			desserts: [
				{
					name: 'Frozen Yogurt',
					calories: 159,
					fat: 6.0,
					carbs: 24,
					protein: 4.0,
					iron: '1%',
				},
				{
					name: 'Ice cream sandwich',
					calories: 237,
					fat: 9.0,
					carbs: 37,
					protein: 4.3,
					iron: '1%',
				},
				{
					name: 'Eclair',
					calories: 262,
					fat: 16.0,
					carbs: 23,
					protein: 6.0,
					iron: '7%',
				},
				{
					name: 'Cupcake',
					calories: 305,
					fat: 3.7,
					carbs: 67,
					protein: 4.3,
					iron: '8%',
				},
				{
					name: 'Gingerbread',
					calories: 356,
					fat: 16.0,
					carbs: 49,
					protein: 3.9,
					iron: '16%',
				},
				{
					name: 'Jelly bean',
					calories: 375,
					fat: 0.0,
					carbs: 94,
					protein: 0.0,
					iron: '0%',
				},
				{
					name: 'Lollipop',
					calories: 392,
					fat: 0.2,
					carbs: 98,
					protein: 0,
					iron: '2%',
				},
				{
					name: 'Honeycomb',
					calories: 408,
					fat: 3.2,
					carbs: 87,
					protein: 6.5,
					iron: '45%',
				},
				{
					name: 'Donut',
					calories: 452,
					fat: 25.0,
					carbs: 51,
					protein: 4.9,
					iron: '22%',
				},
				{
					name: 'KitKat',
					calories: 518,
					fat: 26.0,
					carbs: 65,
					protein: 7,
					iron: '6%',
				},
				{
					name: 'Frozen Yogurt',
					calories: 159,
					fat: 6.0,
					carbs: 24,
					protein: 4.0,
					iron: '1%',
				},
				{
					name: 'Ice cream sandwich',
					calories: 237,
					fat: 9.0,
					carbs: 37,
					protein: 4.3,
					iron: '1%',
				},
				{
					name: 'Eclair',
					calories: 262,
					fat: 16.0,
					carbs: 23,
					protein: 6.0,
					iron: '7%',
				},
				{
					name: 'Cupcake',
					calories: 305,
					fat: 3.7,
					carbs: 67,
					protein: 4.3,
					iron: '8%',
				},
				{
					name: 'Gingerbread',
					calories: 356,
					fat: 16.0,
					carbs: 49,
					protein: 3.9,
					iron: '16%',
				},
				{
					name: 'Jelly bean',
					calories: 375,
					fat: 0.0,
					carbs: 94,
					protein: 0.0,
					iron: '0%',
				},
				{
					name: 'Lollipop',
					calories: 392,
					fat: 0.2,
					carbs: 98,
					protein: 0,
					iron: '2%',
				},
				{
					name: 'Honeycomb',
					calories: 408,
					fat: 3.2,
					carbs: 87,
					protein: 6.5,
					iron: '45%',
				},
				{
					name: 'Donut',
					calories: 452,
					fat: 25.0,
					carbs: 51,
					protein: 4.9,
					iron: '22%',
				},
				{
					name: 'KitKat',
					calories: 518,
					fat: 26.0,
					carbs: 65,
					protein: 7,
					iron: '6%',
				},
			],
		};
	},
	setup() {},
	created() {},
	mounted() {},
	unmounted() {},
	methods: {
		ScrollHeight(e) {
			this.offsetTop5 = e.target.scrollTop;
			document.getElementById('scrollHeight-tbody1').scrollTop =
				this.offsetTop5;
			document.getElementById('scrollHeight-tbody2').scrollTop =
				this.offsetTop5;
		},
	},
};
</script>
<style scoped>
#scrollHeight1 ::v-deep ::-webkit-scrollbar {
	display: none;
}
#scrollHeight1 ::v-deep tbody {
	display: block;
	height: 300px;
	overflow: auto;
}

#scrollHeight1 ::v-deep thead,
tbody tr {
	display: table;
	width: 100%;
	table-layout: fixed;
}

#scrollHeight2 ::v-deep tbody {
	display: block;
	height: 300px;
	overflow: auto;
}

#scrollHeight2 ::v-deep thead,
tbody tr {
	display: table;
	width: 100%;
	table-layout: fixed;
}
</style>
