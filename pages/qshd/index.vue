<template>
	<view>
		<qshd v-if="qshdDefine&&!hdqsDefine" @qshdReturn="getqshd"></qshd>
		<sjkh v-if="sjkhDefine&&!hdqsDefine" @sjkhDefine="getsjkh"></sjkh>
		<hdqs v-if="hdqsDefine" @hdqsDefine="gethdqs"></hdqs>
	</view>
</template>
<script>
	import qshd from "./qshd.vue"
	import sjkh from "./sjkh.vue"
	import hdqs from "./hdqs.vue"
	export default {
		props:{
			tranToqshd:{
				type:Boolean,
				default:false
			}
		},
		components:{qshd,sjkh,hdqs},
		data() {
			return {
				qshdDefine:true,
				sjkhDefine:false,
				hdqsDefine:false
				
				
			}
		},

		watch:{
			tranToqshd:{
				handler(val){
					this.hdqsDefine = val
				}
				
			}
			
		},
		methods: {
			getqshd(data){
				this.qshdDefine = data
				this.sjkhDefine = true
				this.hdqsDefine = false
				this.$emit("SearchReturn", false)
				
			},
			getsjkh(data){
				this.sjkhDefine = data
				this.qshdDefine = true
				this.hdqsDefine = false
				this.$emit("SearchReturn", false)
			},
			gethdqs(data){
				this.hdqsDefine = data
				this.qshdDefine = true
				this.sjkhDefine = false
				this.$emit("SearchReturn", false)
				this.$emit("SearchReturn", false)
			}
			
			
			
		}
	}
</script>
