<template>
	<view style="height: 10%;">
		<!-- <HeaderUse/> -->
		<!-- 签收回单 -->
		<uni-row>
			<uni-col :span="5">
				<button class="littleUseButtonAll" style="background-color: #F1F1F1;color: #3B4144;margin-left: 20rpx;margin-top: 10rpx;margin-bottom: 10rpx;">司机交单</button>
			</uni-col>
			<uni-col :span="5">
				<button class="littleUseButtonAll" @click="dcClick" style="margin-left: 20rpx;margin-top: 10rpx;margin-bottom: 10rpx;">送交客户</button>
			</uni-col>
		</uni-row>
		<uni-row>
			<uni-col :span="8">
				<uni-easyinput id="use" v-model="carOrgoodsNum" placeholder="输入交货号或车号" @iconClick="onClick">
				</uni-easyinput>
			</uni-col>
			<uni-col :span="12">
				<!-- <input type="text" placeholder="起止时间"/> -->
				<view class="example-body">
					<uni-datetime-picker v-model="datetimerange" type="daterange" rangeSeparator="至" />
				</view>
			</uni-col>
			<uni-col :span="4">
				<button class="littleUseButtonAll" @click="searchUse">搜索</button>
			</uni-col>
		</uni-row>
		<uni-card style="margin-top: 10rpx;">
			<uni-table type="selection" @selection-change="change" border stripe emptyText="暂无更多数据"
				style="max-height:750rpx; margin-top: 2%;" :key="1">
				<!-- 表头行 -->
				<uni-tr v-show="true">
					<uni-th align="center" v-for="i,k in header" width="10" :key="k">{{i}}</uni-th>
				</uni-tr>
				<!-- 表格数据行 -->
				<uni-tr v-for="j,nu in listSecond" :key="nu">
					<uni-td v-for="w,index in listSecond[0]" width="40" style="height: 10rpx;" v-if="index!='pz'">
						{{j[index]}}
					</uni-td>
					<uni-td :key="120">
						<uni-tag size="normal" style="width: 60rpx;" inverted="true" :text="j['pz']"
							:type="j['pz']=='已拍'?'primary':'error'"></uni-tag>
					</uni-td>
					<!-- <uni-td :key="120"><button @click="use(j)" style="width: 120rpx;font-size: small;color: #FFFAFA; background-color: rgba(49, 139, 74, 1)">编辑</button></uni-td>
	 -->
				</uni-tr>


			</uni-table>
			<!-- table2 -->
			
		</uni-card>
		<view style="padding-left: 32%; padding-top: 15rpx;"><text style="color: #606266;padding-right: 12rpx;">累计:</text><label style="background-color: #F0F0F0; padding: 8rpx 50rpx 12rpx 50rpx;">{{chooseNum}}</label><text style="color: #606266">份</text>

			<!-- 累计<uni-tag :text="chooseNum+`份`"></uni-tag> -->
		</view>
		<!-- <view>
			<uni-row class="info position-sticky fixed-bottom3">
				<uni-col :span="7">
					<uni-tag :text="`总共`+totalContent+`条`" style="margin-top: 13rpx; margin-left: 90rpx;padding: 0;">
					</uni-tag>
				</uni-col>
				<uni-col :span="11">

					<uni-pagination style="margin-top: 15rpx;font-size: 15rpx; width: 380rpx;" title="标题文字"
						:total="totalContent" @change="paginationChange"></uni-pagination>
				</uni-col>
			</uni-row>
		</view> -->
		<view>
			<button :disabled="chooseNum>0?false:true" @click=" " class="info position-sticky fixed-bottom">签收</button>
			<button type="default" @click="" class="info position-sticky fixed-bottom2">回单导出</button>
		</view>
	</view>
</template>

<script>
	import HeaderUse from "@/components/headerUse/header.vue"
	export default {
		components: {
			HeaderUse
		},
		data() {
			return {
				listThird: [{}],
				carOrgoodsNum: '',
				chooseNum: 0,
				totalContent: 100,
				// styleUse:{height: '100%'},
				datetimerange: [],
				header: ['日期车号', '交货单号', '数量', '起点', '讫点', '单位', '拍照'],
				listSecond: [],
				list: [{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "未拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					}, {
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2022/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "12",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},
					{
						rqch: "2021/05/24苏L12058",
						jhdh: "5564646482",
						sl: "36",
						qd: "1",
						yd: "11",
						dw: "垛",
						pz: "已拍",

					},

				]

			}
		},
		mounted() {
			this.listSecond = this.list
		},
		methods: {
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
			dcClick() {
					this.$emit("qshdReturn", false)

			},
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
					data => !this.datetimerange[0] ||
					(data['rqch'] + "")
					.toLowerCase()
					.includes(this.datetimerange[0].replaceAll("-", "/").toLowerCase())

				)
				// .filter(data => !this.datetimerange[1] ||
				// 	(data['rqch'] + "")
				// 	.toLowerCase()
				// 	.includes(this.datetimerange[1].replaceAll("-", "/").toLowerCase()));
				// }


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

	/deep/ .uni-date-x.uni-date-range {
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
</style>

<!-- style="padding: 0; height: 60rpx; font-size: smaller;background-color: rgba(49, 139, 74, 1);color: #FFFAFA;" -->
