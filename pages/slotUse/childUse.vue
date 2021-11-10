<template>
	<view>
		<slot></slot><br>
		<slot  style="color:blue;" >这是在slot上添加了样式</slot>
		<slot  name="mySlot">这是拥有命名的slot的默认内容</slot>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
