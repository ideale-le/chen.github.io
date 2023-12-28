 <template>
<!--	<view>
		 study center --> 
		<!-- <view class="background">个人中心
		
		</view>
			<view class="box">
				<view class="box_twi">
					<view class="tab">
							 style="display: flex;justify-content: space-around;align-items: center;" -->
						<!--	<view style="width: 200px;height: 40px;display:flex;align-items: center;">
								<img src="../../static/person.jpeg" alt="" style="border-radius: 50%;width: 50%;height: 50px;" />
								<view class="text">
									<text>登录/注册</text>
								</view>
							</view>
					</view>
				</view>
			</view>
			
			<view style="position: absolute;top:25%;left:0px;padding:10px;">
				<img src="../../static/minevip.png" alt="" style="width:100%;"/> 	
			</view> -->
			
			<!-- <view class="box_two" > -->
				<!-- <img src="../../static/minevip.png" alt="" style="width:100%;"/>  -->
				<!-- <view class="box_quan" v-for="(item,index) in card" :key="index">
						<view class="box_ding" > -->
						<!-- 三个  icon+text+icon_right -->
					<!-- 		<view class="box_hang">
								<view class="left_text">
									<i class="iconfont" >&#xeabe;</i>
									<text style="left: 50px;position: absolute;">{{item.text}}</text>
								</view>
								<view class="right_text">
										<i class="iconfont">&#xe622;</i>
								</view>
							</view>
					</view>
				</view>
				
			</view>
	</view> -->
	<view>
		<view class="warp">
			<!-- 播放按钮 -->
			<view class="music"  @click="togglePlay">
				<image v-if="status" mode="widthFix" src="../../static/mucis.png" style="width:70rpx;height:70rpx" mode="widthFix"></image>
				<image  v-else mode="widthFix" src="../../static/music_stop.jpg" style="width:70rpx;height:70rpx" mode="widthFix"></image>
			</view>    
		</view>
	</view>
</template>

<script>
	
	// 			card:[
	// 				{
	// 					text:"我的订单",
	// 				},
	// 				{
	// 					text:"常见问题",
	// 				},
	// 				{
	// 					text:"意见反馈",
	// 				},
	// 				{
	// 					text:"设置",
	// 				},
	// 				{
	// 					text:"分享",
	// 				},
	// 			]
	// 		}
	// 	}	
	// }
	
	
	export default {
		data() {
			return {
				isPlay: false,
				status: true,
				innerAudioContext: null,
				lastRecord: "https://riswein-video.oss-cn-beijing.aliyuncs.com/music/music.mp3",
				};
			}
		},
		//开启音乐
		onShow(){
			this.open()
		},
		//非本页关闭音乐
		onHide(){
			// this.innerAudioContext.pause(); // 停止
			this.pauseAudio();
		},
		//非本页关闭音乐
		onUnload(){
			// this.innerAudioContext.pause(); // 停止
			this.pauseAudio();
		},
		methods: {
			// 播放/暂停音乐
			togglePlay() {
				if (this.isPlay) {
					this.pauseAudio();
				} else {
					this.playVoice();
				}
				this.isPlay = !this.isPlay;
				this.status = !this.status;
			},
			//播放音乐
			open(){
				//播放音乐
				this.innerAudioContext = uni.createInnerAudioContext();
				this.playVoice();
				// this.playVoice('https://riswein-video.oss-cn-beijing.aliyuncs.com/music/music.mp3')
				// uni.$on('changePlay', isPlay => {
				// 	this.playVoice(this.lastRecord, this.isPlay)
				// })
			},
			//播放音乐
			playVoice() { // url即为音频路径
				if (this.lastRecord) {
					this.innerAudioContext.src = this.lastRecord;
					this.innerAudioContext.play();
					this.innerAudioContext.loop = true;
				}
			},
			// 暂停音乐
			pauseAudio() {
				if (this.innerAudioContext) {
					this.innerAudioContext.pause();
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
// 	/* 在线链接服务仅供平台体验和调试使用，平台不承诺服务的稳定性，企业客户需下载字体包自行发布使用并做好备份。 */
// 	@font-face {
// 	  font-family: 'iconfont';  /* Project id 4354390 */
// 	  src: url('//at.alicdn.com/t/c/font_4354390_rubdvahadsi.woff2?t=1701845000134') format('woff2'),
// 	       url('//at.alicdn.com/t/c/font_4354390_rubdvahadsi.woff?t=1701845000134') format('woff'),
// 	       url('//at.alicdn.com/t/c/font_4354390_rubdvahadsi.ttf?t=1701845000134') format('truetype');
// 	}
// 	.iconfont{
// 	    font-family:"iconfont" !important;
// 	    font-size:18px;font-style:normal;
// 	    -webkit-font-smoothing: antialiased;
// 	    -webkit-text-stroke-width: 0.2px;
// 	    -moz-osx-font-smoothing: grayscale;
// 	}
// 	.background{
// 		width:100%;
// 		height: 120px;
// 		background-color:#00dc6c;
// 		color:#fff;
// 		font-size:25x;
// 		padding:20px 0px 0px 0px;
// 		display: flex;
// 		justify-content: center;
// 	}
// 	.box{
// 		padding:10px 10px 10px 10px;
// 		display: flex;
// 		justify-content: space-around;
// 		position: relative;
// 		left:0;
// 		top:-70px;
// 		// background-color: red;
// 	}
// 	.box_twi{
// 		background-color: #fffbff;
// 		width: 100%;
// 		height: 70px;
// 		border-radius: 10px;
// 		display: flex;
// 		justify-content: flex-start;
// 		font-weight: 300px;
// 		font-size: 20px;
// 		padding:10px;
// 		box-shadow: 10px 10px 10px #ccc;
// 		float:left;
// 		.tab{
// 			width: 35%;
// 			display: flex;
// 			// background-color: red;
// 			align-items: center;
// 			flex-wrap: nowrap;
// 		}
// 		.text{
// 			display: flex;
// 			// background-color: aqua;
// 			width: 150px;
// 			align-items: center;
// 			color:#000;
// 			font-weight: 300px;
// 			font-size: 20px;
// 			padding:10px;
// 		}
// 	}
	
// 	.box_two{
// 		border-radius: 10px;
// 		padding:10px;
// 		.box_quan{
// 			display: flex;
// 			// width: 100%;
// 			flex-direction: column;
// 		}
// 		.box_ding{
// 			display: flex;
// 			background-color: #fffbff;
// 			height:20px;	
// 			justify-content: space-between;
// 			flex-direction: column;
// 			align-items: center;
// 			padding:15px;
// 			box-shadow: 10px 10px 10px #ccc;
// 		}
// 		.box_hang{
// 			width: 100%;
// 			display: flex;
// 			align-items: center;
// 			justify-content: space-between;  // 别动
// 			border-bottom:0.5px solid #ffc;
// 			padding-bottom:10px;
// 		}
// 		.left_text{
// 			display: flex;
// 			justify-content:space-between;
// 			align-items: center;
// 		}
// 		.right_text{
// 			display: flex;
// 			justify-content: space-around;
// 			float: right;
// 			align-items: center;
// 		}
// 	}
// </style> 