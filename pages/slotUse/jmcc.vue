<template>
	<view>
		<slot name="header">1这是拥有命名的slot的默认内容</slot>
		<slot name="main">1这是拥有命名的slot的默认内容</slot>
		<slot name="footer">这是拥有命名的slot的默认内容</slot>
		<slot name="other">这是拥有命名的slot的默认内容</slot>
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
