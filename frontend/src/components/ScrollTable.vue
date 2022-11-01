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
			<v-btn class="ma-3" @click="testScroll">Move</v-btn>
		</v-row>

		<v-row justify="center" align="center" class="pa-3">
			<v-data-table
				ref="target-test"
				id="target-table"
				:headers="headers"
				:items="desserts"
				class="overflow-y-auto elevation-1"
				:disable-pagination="true"
				height="300px"
			>
				<template v-slot:body="{ items }">
					<tbody>
						<tr v-for="item in items" :key="item.name">
							<td>{{ item.name }}</td>
						</tr>
					</tbody>
				</template>
			</v-data-table>
		</v-row>

		<v-row justify="center" align="center" class="pa-5">
			<v-subheader>Offset Top3</v-subheader>
			{{ offsetTop3 }}
			<v-btn class="ma-5" @click="testFunc">TEST</v-btn>
		</v-row>
		<v-row justify="center" align="center" class="pa-3">
			<v-col>
				<v-data-table
					ref="target1"
					id="table1"
					:headers="headers"
					:items="desserts"
					class="overflow-y-auto elevation-1"
					:disable-pagination="true"
					height="300px"
					@scroll.passive="testScroll"
				></v-data-table>
			</v-col>
			<v-col>
				<v-data-table
					ref="target2"
					id="table2"
					:headers="headers"
					:items="desserts"
					class="overflow-y-auto elevation-1"
					:disable-pagination="true"
					height="300px"
				></v-data-table>
			</v-col>
		</v-row>

		<v-row justify="center" align="center" class="pa-5">
			<v-subheader>Offset Top1</v-subheader>
			{{ offsetTop1 }}
		</v-row>
		<v-container
			id="scroll-target"
			style="max-height: 400px; border: 2px solid black"
			class="overflow-y-auto"
			@scroll.passive="testScroll"
		>
			<v-row align="center" justify="center" style="height: 1000px"> </v-row>
		</v-container>
		<v-row justify="center" align="center" class="pa-5">
			<v-subheader>Offset Top4</v-subheader>
			{{ offsetTop4 }}
			<v-btn @click="testFunc">TEST</v-btn>
		</v-row>
		<!-- 여기서부터 되는 코드임 -->
		<v-data-table
			:headers="headers"
			:disable-pagination="true"
			:hide-default-footer="true"
		>
			<template v-slot:no-data> <tr style="display: none" /></template>
		</v-data-table>
		<div id="target-div" style="height: 200px; overflow: scroll">
			<v-data-table
				id="please"
				ref="please"
				:headers="headers"
				:items="desserts"
				class="overflow-y-auto elevation-1"
				:disable-pagination="true"
			>
				<template v-slot:header="{ props }">
					<thead>
						<tr>
							<th
								class="fixedHeader"
								v-for="head in props.headers"
								:key="head.value"
							>
								{{ head.text }}
							</th>
						</tr>
					</thead>
				</template>
			</v-data-table>
		</div>

		<div class="pa-4"></div>
		<div class="container">
			<table id="customTable">
				<thead>
					<th class="fixedHeader">name</th>
					<th class="fixedHeader">no</th>
					<th class="fixedHeader">dept</th>
					<th class="fixedHeader">kya</th>
				</thead>
				<tbody>
					<tr v-for="item in desserts" :key="item.name">
						<td>h{{ item.name }}</td>
						<td>h{{ item.calories }}</td>
						<td>h{{ item.fat }}</td>
						<td>h{{ item.carbs }}</td>
					</tr>
				</tbody>
			</table>
		</div>
	</div>
</template>
<script>
export default {
	components: {},
	name: 'ScrollTable',
	data() {
		return {
			target: null,
			offsetTop1: 0,
			offsetTop2: 0,
			offsetTop3: 0,
			offsetTop4: 0,
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
	mounted() {
		this.target = document.querySelector('#target-div');
		this.target.addEventListener('scroll', this.handleScroll);
	},
	unmounted() {},
	methods: {
		handleScroll(e) {
			var scrollTop = e.target.scrollTop;
			console.log(scrollTop);
		},

		onScroll(e) {
			this.offsetTop1 = e.target.scrollTop;
		},
		onScrollTable(e) {
			this.offsetTop2 = e.target.scrollTop;
		},
		onScrollTable2() {
			console.log('onScrollTable2...');
			console.log(this.offsetTop3);
		},
		testScroll(e) {
			console.log('testScroll()..');
			this.offsetTop3 = e.target.scrollTop;
		},
		testFunc() {
			var t = document.getElementById('target-div').scrollTop;
			console.log(t);
			console.log(this.$refs.please);
		},
	},
};
</script>
<style>
.container {
	height: 300px;
	overflow: auto;
}

.fixedHeader {
	position: -webkit-sticky;
	position: sticky;
	top: 0px;
	background-color: yellow;
}
</style>
