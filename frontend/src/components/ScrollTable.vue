<template>
	<div>
		<v-row justify="center" align="center" class="pa-5">
			<v-subheader>Offset Top1</v-subheader>
			{{ offsetTop1 }}
		</v-row>
		<v-container
			id="scroll-target"
			style="max-height: 400px; border: 2px solid black"
			class="overflow-y-auto"
		>
			<v-row
				v-scroll:#scroll-target="onScroll"
				align="center"
				justify="center"
				style="height: 1000px"
			>
			</v-row>
		</v-container>

		<!-- scrollbar가 두개 생겼음 -->
		<v-row justify="center" align="center" class="pa-5">
			<v-subheader>Offset Top2</v-subheader>
			{{ offsetTop2 }}
		</v-row>
		<div
			id="scroll-table"
			style="max-height: 400px; border: 2px solid black"
			class="overflow-y-auto"
		>
			<v-data-table
				:headers="headers"
				:items="desserts"
				class="elevation-1"
				:disable-pagination="true"
				height="500px"
				:fixed-header="true"
				v-scroll:#scroll-table="onScrollTable"
			>
			</v-data-table>
		</div>
		<v-row justify="center" align="center" class="pa-5">
			<v-subheader>Offset Top3</v-subheader>
			{{ offsetTop3 }}
		</v-row>
		<v-row justify="center" align="center" class="pa-5">
			<v-data-table
				id="target-table"
				:headers="headers"
				:items="desserts"
				class="elevation-1"
				:disable-pagination="true"
				height="300px"
				:fixed-header="true"
				v-scroll:#target-table="onScrollTable2"
			>
				<template v-slot:tbody>
					<tbody></tbody>
				</template>
			</v-data-table>
		</v-row>
	</div>
</template>
<script>
export default {
	components: {},
	name: 'ScrollTable',
	data() {
		return {
			offsetTop1: 0,
			offsetTop2: 0,
			offsetTop3: 0,
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
			],
		};
	},
	setup() {},
	created() {},
	mounted() {},
	unmounted() {},
	methods: {
		onScroll(e) {
			this.offsetTop1 = e.target.scrollTop;
		},
		onScrollTable(e) {
			this.offsetTop2 = e.target.scrollTop;
		},
		onScrollTable2(e) {
			console.log(e);
			this.offsetTop3 = e.target.scrollTop;
		},
	},
};
</script>
