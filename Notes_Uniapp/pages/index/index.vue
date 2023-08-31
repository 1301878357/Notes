<template>
	<view>
		<home :cur="PageCur" v-if="PageCur=='home'" :key="commponent1Key"></home>
		<accounting v-if="PageCur=='accounting'" :key="commponent2Key" :modalName="modalName" ref="accounting"></accounting>
		<people v-if="PageCur=='people'" :key="commponent3Key"></people>
		<view class="cu-bar tabbar bg-white shadow foot">
			<view :class="PageCur=='home'?'action text-green':'action text-gray'" @click="NavChange" data-cur="home">
				<view class='cuIcon-homefill'></view>主页
			</view>
			<view :class="PageCur=='accounting'?'action text-green':'action text-gray'" @click="showModal" data-cur="accounting">
				<view class='iconfont icon-jiahao1'></view>+
			</view>
			<view :class="PageCur=='people'?'action text-green':'action text-gray'" @click="NavChange" data-cur="people">
				<view class='cuIcon-people'></view>个人
			</view>
		</view>
	</view>
</template>

<script>
	import accounting from '../accounting/accounting.vue'
	export default {
		components: {
			accounting,
		},
		data() {
		return {
				PageCur: 'home',
				commponent1Key: 0,
				commponent2Key: 0,
				commponent3Key: 0,
			}
		},
		onLoad:function(){
			this.PageCur='home'
			++this.commponent1Key
			++this.commponent2Key
			++this.commponent3Key
		},
		methods: {
			NavChange: function(e) {
				this.PageCur = e.currentTarget.dataset.cur
			},
			showModal: function(e){
				// this.modalName = "accounting";
				// ++this.commponent2Key
				// this.PageCur = e.currentTarget.dataset.cur
				uni.navigateTo({
					url: `/pages/accounting/accounting`
				})
			}
			
			
		}
	}
</script>

<style>
	image {
		width: 50rpx;
		height: 50rpx;
	}
</style>
