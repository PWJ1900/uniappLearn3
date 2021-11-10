<template>
	<view @click="sdf">
		<HeaderUse/>
		fdsafas
	</view>
</template>

<script>
	import HeaderUse from "@/components/headerUse/header.vue"
	export default {
		components:{HeaderUse},
		data() {
			return {
			}
		},
		methods: {
			sdf(){
				uni.navigateBack({
					
				})
			}
			
		}
	}
</script>

<style>

</style>
