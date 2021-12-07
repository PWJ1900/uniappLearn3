<template>
	<view style="height: 10%;">
		<!-- <HeaderUse/> -->
		<!-- 签收回单 -->
		<uni-row>
			<uni-col :span="8">
				<uni-easyinput id="use" v-model="carOrgoodsNum" placeholder="输入客户查询">
				</uni-easyinput>
			</uni-col>
			<uni-col :span="12">
				<!-- <input type="text" placeholder="起止时间"/> -->
				<view class="example-body">
					<uni-datetime-picker v-model="datetime" type="date"/>
				</view>
			</uni-col>
			<uni-col :span="4">
				<button class="littleUseButtonAll" @click="searchUse">搜索</button>
			</uni-col>
		</uni-row>
		<uni-card style="margin-top: 10rpx;">
			<vTable :columns="header"  :td-height="45" :fixed-checkbox="true" :list="listSecond" :tableHeightUse="useTableStyle" selection="mulit" @on-selection-change="onSelectionChange"></vTable>
			
			<!-- <uni-table type="selection" @selection-change="change" border stripe emptyText="暂无更多数据"
				style="max-height:750rpx; margin-top: 2%;" :key="1">
				<uni-tr>
					<uni-th align="center" v-for="i,k in header" width="10" :key="k">{{i}}</uni-th>
				</uni-tr>
				<uni-tr v-for="j,nu in listSecond" :key="nu">
					<uni-td v-for="w,index in listSecond[0]" width="40" style="height: 10rpx;" v-if="index!='pz'">
						{{j[index]}}
					</uni-td>
					<uni-td :key="120">
						<uni-tag size="normal" style="width: 60rpx;" inverted="true" :text="j['pz']"
							:type="j['pz']=='已拍'?'primary':'error'"></uni-tag>
					</uni-td>
				</uni-tr>


			</uni-table> -->
			
			
		</uni-card>
	<view style="padding-left: 32%; padding-top: 15rpx;"><text style="color: #606266;padding-right: 12rpx;z-index: 1000;">累计:</text><label style="background-color: #F0F0F0; padding: 8rpx 50rpx 12rpx 50rpx;">{{chooseNum}}</label><text style="color: #606266">份</text>
		</view>
		<view>
				<button :disabled="chooseNum>0?false:true" @click="popShare" class="info position-sticky fixed-bottom">分享</button>
		</view>
	</view>
</template>

<script>
	import vTable from '../../components/no-bad-table/table.vue'
		export default {
		components:{vTable},
		data() {
			return {
				tableHeight:'',
				listThird: [{}],
				carOrgoodsNum: '',
				chooseNum: 0,
				totalContent: 100,
				// styleUse:{height: '100%'},
				datetime: '',
				header: [{key:'rqch',title:'日期车号',$fixed:"left"}, {key:'jhdh',title:'交货单号'}, {key:'sl',title:'数量'}, {key:'qd',title:'起点'}, {key:'yd',title:'讫点'}, {key:'dw',title:'单位'}, {key:'dateTime',title:'签收日期'}],
				listSecond: [],
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
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						dateTime: "2021.1.1",

					},

				]

			}
		},
		mounted() {
			this.listSecond = this.list
			console.log("这是"+this.tableHeight)
			uni.getSystemInfo({
				success:(res)=> {
					console.log(res.windowHeight)
					this.tableHeight = res.windowHeight - 200
					console.log(this.tableHeight)
					
				}
			})
		},
		computed:{
			useTableStyle(){
				return  'max-height:'+ this.tableHeight + 'px'
			}
			
		},
		
		methods: {
			onSelectionChange(obj){
				this.chooseNum = obj.new.length
				console.log("对比前后，选中的变化")
				console.log(obj)
			},
			change(e) {
				console.log(e)
				this.chooseNum = e.detail.index.length
				let k = 0
				for (let i in this.list) {
					for (let j in e.detail.index) {
						if (i == j) {
							this.listThird[k] = this.list[i]
							k++
						}

					}
				}


				console.log(this.listThird)
			},
			use(e) {
				console.log(e)

			},
			
			// dcClick() {
			


			// },
			searchUse() {
				// console.log(this.datetimerange[0].replaceAll("-","/"))
				// if (this.datetimerange=='' || this.carOrgoodsNum.length<=0) {
				// 	this.list = this.listSecond
				// }else{
				this.listSecond = this.list.filter( //便编写的查询过滤器考虑把次放出去因为每个的页面需要的过滤属性不一样
					(data) =>
					!this.carOrgoodsNum ||
					(data['rqch'] + "")
					.toLowerCase()
					.includes(this.carOrgoodsNum.toLowerCase())

				).filter(
					data => !this.datetime ||
					(data['rqch'] + "")
					.toLowerCase()
					.includes(this.datetime.replaceAll("-", "/").toLowerCase())

				)
				// .filter(data => !this.datetimerange[1] ||
				// 	(data['rqch'] + "")
				// 	.toLowerCase()
				// 	.includes(this.datetimerange[1].replaceAll("-", "/").toLowerCase()));
				// }


			},
			popShare(){
				// this.$refs.popup.show()
				uni.share({
				    provider: "weixin",
				    scene: "WXSceneSession",
				    type: 1,
				    summary: this.listThird,
				    success: function (res) {
				        console.log("success:" + JSON.stringify(res));
				    },
				    fail: function (err) {
				        console.log("fail:" + JSON.stringify(err));
				    }
				});
			}
		}
	}
</script>

<style>
	.uni-input-placeholder {
		font-size: xx-small !important;
	}

	.uni-input-input {
		font-size: xx-small !important;
	}

	/deep/ .uni-date-x.uni-date-single{
		height: 57rpx;
	}
	

	/deep/ .uni-easyinput__content.is-input-border {
		height: 60rpx !important;
		min-height: 0;
	}

	.position-sticky {
		position: -webkit-sticky !important;
		position: sticky !important;
	}

	.fixed-bottom {
		position: fixed !important;
		height: 80rpx;
		margin-left: 0;
		background-color: rgba(49, 139, 74, 1);
		font-size: large;
		color: #FFFAFA;
		right: 0;
		bottom: calc(var(--window-bottom) + 3px);
		left: 0;
		margin-bottom: 6;
	}

	.fixed-bottom2 {
		position: fixed !important;
		width: 80px;
		height: 30px;
		margin-right: 10rpx;
		background-color: rgba(49, 139, 74, 1);
		font-size: small;
		color: #FFFAFA;
		right: 0;
		bottom: calc(var(--window-bottom) + 130rpx);
		left: 0;
		margin-bottom: 6;
	}

	.fixed-bottom3 {
		position: fixed !important;
		margin-right: 10rpx;
		font-size: small;
		right: 0;
		bottom: calc(var(--window-bottom) + 180rpx);
		left: 0;
		margin-bottom: 6;
	}

	.uni-card.uni-border {
		/* max-height: 1000px; */
		margin: 0;
	}

	.littleUseButtonAll {
		padding: 0;
		height: 60rpx;
		font-size: smaller;
		background-color: rgba(49, 139, 74, 1);
		color: #FFFAFA;

	}
	/deep/ .uni-date__icon-clear{
		margin-top: -12rpx !important;
		
	}
</style>

<!-- style="padding: 0; height: 60rpx; font-size: smaller;background-color: rgba(49, 139, 74, 1);color: #FFFAFA;" -->
