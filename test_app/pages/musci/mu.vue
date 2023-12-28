<template>
	<view class="warp">
		<!-- 播放按钮 -->
		<view class="music" :class="{ran:status}" @click="playVoice(lastRecord,isPlay)">
			<image src="../../static/mucis.png" style="width:70rpx;height:70rpx" mode="widthFix"></image>
		</view>    
	</view>
</template>

<script>
	export default {
		data() {
			return {
				//播放器
				isPlay: false,
				status: true
			}
		},
		//开启音乐
		onShow(){
			this.open()
		},
		//非本页关闭音乐
		onHide(){
			this.innerAudioContext.pause(); // 停止
		},
		//非本页关闭音乐
		onUnload(){
			this.innerAudioContext.pause(); // 停止
		},
		methods: {
			//播放音乐
			open(){
				//播放音乐
				this.innerAudioContext = uni.createInnerAudioContext();
				this.playVoice('https://riswein-video.oss-cn-beijing.aliyuncs.com/music/music.mp3')
				uni.$on('changePlay', isPlay => {
					this.playVoice(this.lastRecord, this.isPlay)
				})
			},
			//播放音乐
			playVoice(url, isPlay) { // url即为音频路径
				if (url) {
					this.lastRecord = url; // 将路径赋值给定义的变量好做判断
					this.innerAudioContext.src = url; // 配置音频播放路径
					this.innerAudioContext.play(); // 播放
					this.innerAudioContext.loop = true; // 是否循环播放
				}
				 this.isPlay = !this.isPlay;
				if (isPlay) {
					this.innerAudioContext.pause(); // 停止
					this.status = false
				}else{
					this.status= true
				}
			}
		}
	}
	
</script>

<style>
</style>