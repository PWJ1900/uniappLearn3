<template>
	<view>
		<uni-card style="margin-top: 10rpx;">
			<vTable :columns="header"  :td-height="45" :fixed-checkbox="true" :list="list" :tableHeightUse="useTableStyle" selection="mulit" @on-selection-change="onSelectionChange" :row-class-name="rowClassNameFn"></vTable>
			<!-- <uni-table type="selection" @selection-change="change" border stripe emptyText="暂无更多数据"
				style="max-height:750rpx; margin-top: 2%;" :key="1"> -->
				<!-- 表头行 -->
				<!-- <uni-tr>
					<uni-th align="center" v-for="i,k in header" width="10" :key="k">{{i}}</uni-th>
				</uni-tr> -->
				<!-- 表格数据行 -->
				<!-- <uni-tr v-for="j,nu in list" :key="nu"
					:style="colorIndex.includes(nu)?`background-color: #4CD964;`:``">
					<uni-td v-for="w,index in list[0]" width="40" style="height: 10rpx;" v-if="index!='pz'">
						{{j[index]}}
					</uni-td>
					<uni-td :key="120">
						<uni-tag size="normal" style="width: 60rpx;" inverted="true" :text="j['pz']"
							:type="j['pz']=='已拍'?'primary':'error'"></uni-tag>
					</uni-td>
				</uni-tr> -->


			<!-- </uni-table> -->
			<!-- table2 -->

		</uni-card>
		<button style="width: 200rpx;font-size: smaller;margin-right: 0;" @click="popShare()">分享</button>

	</view>
</template>

<script>
	import vTable from '../../components/no-bad-table/table.vue'
	export default {
		components:{vTable},
		onLoad(option) {
			if(option.item)
			this.colorIndex = JSON.parse(decodeURIComponent(option.item))
		},
		data() {
			return {
				colorIndex: [],
				listUse:[{}],
				tableHeight:'',
				header: [{key:'rqch',title:'日期车号'}, {key:'jhdh',title:'交货单号'}, {key:'sl',title:'数量'}, {key:'qd',title:'起点'}, {key:'yd',title:'讫点'}, {key:'dw',title:'单位'}, {key:'dateTime',title:'签收日期'}],
				list: [{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2022/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "12",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646481",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",
				
					},
				
				]
					}},
					computed:{
						useTableStyle(){
							return  'max-height:'+ this.tableHeight + 'px'
						}
						
					},
					mounted() {
						this.listSecond = this.list
						console.log("这是"+this.tableHeight)
						uni.getSystemInfo({
							success:(res)=> {
								console.log(res.windowHeight)
								this.tableHeight = res.windowHeight - 130
								console.log(this.tableHeight)
								
							}
						})
					},
				methods: {
					popShare() {
						uni.share({
							provider: "weixin",
							scene: "WXSceneSession",
							type: 1,
							summary: "我正在使用HBuilderX开发uni-app，赶紧跟我一起来体验！",
							success: function(res) {
								console.log("success:" + JSON.stringify(res));
							},
							fail: function(err) {
								console.log("fail:" + JSON.stringify(err));
							}
						});
					
					},
					rowClassNameFn(row, index){
						console.log(this.colorIndex)
						if (this.colorIndex.includes(index)) {
							return 'demo-table-info-row';
						}
						return '';
					}

				}
			}
</script>

<style>

</style>
