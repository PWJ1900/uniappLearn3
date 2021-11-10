<template>
	<view>
		<view>
			<view class="example-body">
			            <uni-datetime-picker
			                v-model="datetimerange"
			                type="datetimerange"
			                rangeSeparator="至"
			            />
			        </view>
				<!-- 	start="2021-3-20 12:00:00"
					end="2021-6-20 20:00:00" -->
			<v-tabs v-model="current" :tabs="tabs" @change="changeTab"></v-tabs>		
			<uni-easyinput type="number[]" v-model="dd" style="width: 100px;"></uni-easyinput>
			<form @submit="formSubmit" @reset="formReset">
				<!-- <view class="uni-form-item uni-column" style="display: flex;"> -->
				<uni-row>
					<uni-col :span="12">
					<view class="title" style="width: 50%;">switch</view>
					</uni-col>
					<uni-col :span="12">
					<view>
						<switch name="switch" />
					</view>
					</uni-col>
					</uni-row>
					<view class="uni-list">
						<view class="uni-list-cell">
							<view class="uni-list-cell-db">
								<picker @change="bindPickerChange" :value="index" :range="array">
									<view class="uni-input"><button>{{array[index]}}</button></view>
								</picker>
							</view>
						</view>
					</view>
				<!-- </view> -->
				<view class="uni-form-item uni-column">
					<view class="title">radio</view>
					<radio-group name="radio">
						<label>
							<radio value="radio1" /><text>选项一</text>
						</label>
						<label>
							<radio value="radio2" /><text>选项二</text>
						</label>
					</radio-group>
				</view>
				<view class="uni-form-item uni-column">
					<view class="title">checkbox</view>
					<checkbox-group name="checkbox">
						<label>
							<checkbox value="checkbox1" /><text>选项一</text>
						</label>
						<label>
							<checkbox value="checkbox2" /><text>选项二</text>
						</label>
					</checkbox-group>
				</view>
				<view class="uni-form-item uni-column">
					<view class="title">slider</view>
					<slider value="50" name="slider" show-value></slider>
				</view>
				<view class="uni-form-item uni-column">
					<view class="title">input</view>
					<input class="uni-input" name="input" placeholder="这是一个输入框" />
				</view>
				<view class="uni-btn-v">
					<button form-type="submit">Submit</button>
					<button type="default" form-type="reset">Reset</button>
				</view>
			</form>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				datetimerange: ["2021-03-20 20:10:10", "2021-05-10 10:10:10"],
				dd:[1,3,4],
				array: ['中国', '美国', '巴西', '日本'],
				index:0,current: 0,
      tabs: ['军事', '国内', '新闻新闻', '军事', '国内', '新闻', '军事', '国内', '新闻']
 
			}
		},
		methods: {
			changeTab(index) {
			  console.log('当前选中的项：' + index)
			},
			formSubmit: function(e) {
				console.log('form发生了submit事件，携带数据为：' + JSON.stringify(e.detail.value))
				var formdata = e.detail.value
				uni.showModal({
					content: '表单数据内容：' + JSON.stringify(formdata),
					showCancel: false
				});
			},
			formReset: function(e) {
				console.log('清空数据')
			},
			bindPickerChange: function(e) {
			            console.log('picker发送选择改变，携带值为', e.target.value)
			            this.index = e.target.value
			        },
		}
	}
</script>

<style>
	.uni-form-item .title {
		padding: 20rpx 0;
	}
</style>
