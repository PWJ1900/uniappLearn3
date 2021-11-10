<template>
	<view>
		<view v-if="!isJumpTable">
			<uni-card style="margin-top: 10rpx;">
						<uni-table type="selection" @selection-change="change" border stripe emptyText="暂无更多数据"
							style="max-height:750rpx; margin-top: 2%;" :key="1">
							<!-- 表头行 -->
							<uni-tr>
								<uni-th align="center" v-for="i,k in header" width="10" :key="k">{{i}}</uni-th>
							</uni-tr>
							<!-- 表格数据行 -->
							<uni-tr v-for="j,nu in list" :key="nu">
								<uni-td v-for="w,index in list[0]" width="40" style="height: 10rpx;" v-if="index!='pz'">
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
					<button style="width: 200rpx;font-size: smaller;margin-right: 0;" @click="tableReturn">返回</button>
					
		</view>
	<view  v-if="isJumpTable">
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
				<button class="littleUseButtonAll" @click="">搜索</button>
			</uni-col>
		</uni-row>
		<uni-card note="true" style="height: 190rpx; padding: 0 !important;">
			<uni-row>
				<uni-col :span="19">
								<text style="font-size: smaller;">客户签收</text>
				</uni-col>
				<uni-col :span="5">
					<text style="font-size: smaller;">5月25日</text>
				</uni-col>
				
			</uni-row>
			<uni-row style="margin-bottom: 0;">
				<uni-col :span="20">
					<text style="font-size: larger;" space="emsp">50</text>份
				</uni-col>
				<uni-col :span="4">
					<uni-icons type="forward" size="30" @click="tableReturn()"></uni-icons>
				</uni-col>
			</uni-row>

			    <template v-slot:footer>
			        <view class="footer-box">
			        
			        </view>
			    </template>
		</uni-card>
		<button style="width: 200rpx;font-size: smaller;margin-right: 0;" @click="$emit('hdqsDefine',false)">返回</button>
	</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				datetimerange:[],
				carOrgoodsNum:'',
				isJumpTable:true,
				header: ['日期车号', '交货单号', '数量', '起点', '讫点', '单位', '拍照'],
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
		methods: {
			tableReturn(){
				this.isJumpTable = !this.isJumpTable
			}
			
		}
	}
</script>

<style>
.littleUseButtonAll {
		padding: 0;
		height: 60rpx;
		font-size: smaller;
		background-color: rgba(49, 139, 74, 1);
		color: #FFFAFA;
	}
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
	
</style>
