<template>
	<view class="content">
		<view>
			标题占位 
		</view>
		<view>
			标题占位 
		</view>
		<view>
			标题占位 
		</view>
		<view> 
			标题占位 
		</view>
		<LiFilter @change="change" @select="select" :datalist="datalist" :height="height"></LiFilter>
		<view 
			v-bind:key="item.value" 
			v-for="item in testList">
			{{ item.text }} 
		</view>
	</view>
</template>

<script>
import LiFilter from '@/components/Li-Filter/Li-Filter.vue';
 
export default {
	components: {
		LiFilter
	},
	data() {
		return {
			datalist: {},
			testList: {},
			height: 0.6,
			title: 'Hello'
		};
	},
	onLoad() {
		this.testList = [];
		for (var i = 0; i < 30; i++) {
			this.testList.push({
				value: i,
				text: 'test data' + i,
				time: new Date()
			});
		}
		let tempdata = {
			filterType: 1,
			data: []
		};

		let normalItem = {
			title: '综合排序', //排序头的名称
			value: 'a',
			type: 1, //类型，0：没有下拉选项，1：单项下拉列表，2：多项列表，如地区选择
			data: [
				{
					value: 1,
					text: '综合排序'
				},
				{
					value: 2,
					text: '只看商家'
				},
				{
					value: 3,
					text: '只看产品'
				}
			]
		};

		let sigleItem = {
			title: '销量', //排序头的名称
			value: 'b',
			type: 0 //类型，0：没有下拉选项，1：单项下拉列表，2：多项列表，如地区选择
		};

		let areaData = require('../..//static/area.json');
		let typeData = require('../..//static/type.json');

		let AreaItem = {
			title: '区域', //排序头的名称
			value: 'c',
			type: 2, //类型，0：没有下拉选项，1：单项下拉列表，2：多项列表，如地区选择
			data: areaData
		};

		let typeItem = {
			title: '类型', //排序头的名称
			value: 'd',
			type: 2, //类型，0：没有下拉选项，1：单项下拉列表，2：多项列表，如地区选择
			data: typeData
		};

		tempdata.data.push(normalItem);
		tempdata.data.push(sigleItem);
		tempdata.data.push(AreaItem);
		tempdata.data.push(typeItem);
		this.datalist = tempdata;
	},
	methods: {
		change(e) {
			console.log('----------change----------');
			console.log(e);
		},
		select(e) {
			console.log('----------select----------');
			console.log(e);
		}
	}
};
</script>

<style></style>
