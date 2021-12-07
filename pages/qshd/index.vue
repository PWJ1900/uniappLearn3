<template>
	<view style="height: 10%;">
		<!-- <HeaderUse/> -->
		<!-- 签收回单 -->
		<uni-row>
			<uni-col :span="5">
				<button class="littleUseButtonAll"
					style="background-color: #F1F1F1;color: #3B4144;margin-left: 20rpx;margin-top: 10rpx;margin-bottom: 10rpx;width: 150rpx;">司机交单</button>
			</uni-col>
			<uni-col :span="14">
				<button class="littleUseButtonAll" @click="dcClick"
					style="margin-left: 20rpx;margin-top: 10rpx;margin-bottom: 10rpx; width: 150rpx;">送交客户</button>
			</uni-col>
			<uni-col :span="5">
				<button class="littleUseButtonAll" @click="historySearch"
					style="margin-left: 20rpx;margin-top: 10rpx;margin-bottom: 10rpx;">历史查询</button>
			</uni-col>
		</uni-row>
		<uni-row>
			<uni-col :span="8">
				<uni-easyinput id="use" v-model="carOrgoodsNum" placeholder="输入交货号或车号">
				</uni-easyinput>
			</uni-col>
			<uni-col :span="12">
				<!-- <input type="text" placeholder="起止时间"/> -->
				<view class="example-body">
					<uni-datetime-picker v-model="datetime" type="date" />
				</view>
			</uni-col>
			<uni-col :span="4">
				<button class="littleUseButtonAll3" @click="searchUse" ref="client">搜索</button>
			</uni-col>
		</uni-row>
		<uni-card style="margin-top: 10rpx;background: #d1d1d1;" >
			<vTable :columns="header"  :td-height="45" :fixed-checkbox="true" :list="listSecond" :tableHeightUse="useTableStyle" selection="mulit" @on-selection-change="onSelectionChange" @edi="ediFn" :slot-cols="['pz']">
				<!-- <template v-slot="{ row }">
					<view style="font-weight: blod;color:red;">{{ `hao`}}</view>
				</template> -->
				
			</vTable>
		</uni-card>
		<view style="padding-left: 32%; padding-top: 15rpx;"><text
				style="color: #606266;padding-right: 12rpx;">累计:</text><label
				style="background-color: #F0F0F0; padding: 8rpx 50rpx 12rpx 50rpx;">{{chooseNum}}</label><text
				style="color: #606266">份</text>
		</view>
		<view>
			<button :disabled="chooseNum>0?false:true" @click=" " class="info position-sticky fixed-bottom" >签收</button>
			<button type="default" @click="useIII" id="usehddc" class="info position-sticky fixed-bottom2"  ref="hddcClient">回单导出</button>
		</view>
	</view>
</template>

<script>
	import vTable from '../../components/no-bad-table/table.vue'
	export default {
		onLoad() {
			
		},
		// onReady(){// 注意：想要拿到元素实例，需要在实例已经挂载到页面上才可以
			// console.log(this.$refs.hddcClient.$el.getBoundingClientRect().top)
		
		// this.tableHeight = this.$refs.hddcClient.$el.getBoundingClientRect().top-this.$refs.client.$el.getBoundingClientRect().bottom-30
		
		// console.log("hello")
			// },
			
		components:{vTable},
		data() {
			return {
				listThird: [{}],
				carOrgoodsNum: '',
				chooseNum: 0,
				tableHeight:'',
				totalContent: 100,
				datetime: '',
				 // {key:'pz',title:'拍照'}
				header: [{key:'rqch',title:'日期车号',$fixed:"left"}, {key:'jhdh',title:'交货单号'}, {key:'sl',title:'数量'}, {key:'qd',title:'起点'}, {key:'yd',title:'讫点'}, {key:'dw',title:'单位'},{
						title: "拍照",
						key: "$operate",
						$operateList: [
							{
								label: "编辑",
								event: "edi",
								id: "edi"
							}
						]
					}],
				listSecond: [],
				list: [{
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
								
									},{
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
						pz: "补拍",

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
					this.tableHeight = res.windowHeight - 200
					console.log(this.tableHeight)
					
				}
			})
			

		},
		methods: {
			// getInfo() {
			// 				const query = uni.createSelectorQuery().in(this);
			// 				query.select('#hdqsId').boundingClientRect(data => {
			// 					console.log(JSON.stringify(data))
			// 				}).exec();
			// 			},
			onSelectionChange(obj){
				this.chooseNum = obj.new.length
				console.log("对比前后，选中的变化")
				console.log(obj)
			},
			use(e) {
				console.log(e)

			},
			dcClick() {
				uni.navigateTo({
					url:"./sjkh"
				})

			},
			historySearch(){
				uni.navigateTo({
					url:"./hdqs"
				})
			},
			ediFn(data) {
				console.log(data)
				if(data.row.pz == '补拍'){
					uni.chooseImage({
						count: 9,
						sizeType: ['original', 'compressed'],
						sourceType: ['camera'], //这要注意，camera掉拍照，album是打开手机相册
						success: (res) => {
							// console.log(res);
							// const tempFilePaths = res.tempFilePaths;
							// this.zp = res.tempFilePaths[0];
							// console.log(this.zp)
							this.list.push(res.tempFilePaths[0])
							console.log(res.tempFilePaths[0])
							// console.log(this.list)
					
						}
					});
					
				}else{
					
				}
				uni.showToast({
					title: `编辑第${data.index}行`,
					duration: 800
				});
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
					.includes(this.carOrgoodsNum.toLowerCase()) || (data['jhdh'] + "")
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
			useIII(){
				

				
			}
		}
	}
</script>

<style scoped>
	.uni-input-placeholder {
		font-size: xx-small !important;
	}

	.uni-input-input {
		font-size: xx-small !important;
	}

	/* 	/deep/ .uni-date-x.uni-date-range {
		height: 57rpx;
	} */
	/deep/ .uni-date-x.uni-date-single {
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
		bottom: calc(var(--window-bottom) + 120rpx);
		left: 0;
	
	}

	.fixed-bottom3 {
		position: fixed !important;
		margin-right: 10rpx;
		font-size: small;
		right: 0;
		bottom: calc(var(--window-bottom) + 180rpx);
		left: 0;
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
	.littleUseButtonAll3 {
		padding: 0;
		height: 60rpx;
		font-size: smaller;
		background-color: rgba(49, 139, 74, 1);
		color: #FFFAFA;
	
	}

	/deep/ .uni-date__icon-clear {
		margin-top: -12rpx !important;

	}
</style>

<!-- style="padding: 0; height: 60rpx; font-size: smaller;background-color: rgba(49, 139, 74, 1);color: #FFFAFA;" -->
