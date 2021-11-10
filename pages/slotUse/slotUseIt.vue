<template>
	<view>
		
		<Child><span style="color:#007AFF;">hello world</span></Child>
		<jmcc> <span slot="header">这是headeraaaa</span>
		<button slot="header">d</button></jmcc>
		<zyycc>
		      <template  v-slot:demo="{text,record}">
		       {{text}}
		       <div v-for="item in record" :key="item">{{item}}</div>
		      </template>
		</zyycc>
	</view>
</template>

<script>
	import Child from './childUse.vue'
	import jmcc from './jmcc.vue'
	import zyycc from './zyycc.vue'
	export default {
		components:{Child,jmcc,zyycc},
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
