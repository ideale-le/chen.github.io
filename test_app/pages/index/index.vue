<!-- 本示例未包含完整css，获取外链css请参考上文，在hello uni-app项目中查看 -->
<template>
	<view class="background">
		
		<!-- 顶部搜索 -->
		<view class="search">
		  <input autoFocus v-model="searchValue" class="search-input" placeholder="输入搜索关键词" />
		  <view class="search-icon">
		    <!-- 这里放置左侧搜索图标，你可以使用iconfont或者本地图片 -->
		    <!-- 示例使用字体图标 -->
			  <img src="../../static/search.png" alt="" style="width:35px;height:35px;">
		    <!-- <text class="iconfont icon-search"></text> -->
		  </view>
		  <view class="Ma">
		  	<img src="../../static/Ma.png" alt="" style="width:40px;height:40px;cursor: pointer;">
		  </view>
		</view>
		<!-- 轮播图 -->
		<view class="uni-margin-wrap">
			<swiper class="swiper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
				:duration="duration">
				<swiper-item>
					<view class="swiper-item">
						<img src="../../static/banner1.png" alt="">
	 				</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<img src="../../static/banner1.png" alt="">
					</view>
				</swiper-item>
				<swiper-item>
					<view class="swiper-item">
						<img src="../../static/banner1.png" alt="">
					</view>
				</swiper-item>
			</swiper>
		</view>	
		
		<!-- 15icon排版 -->
		<!-- <view class="box_there">
			<view class="box_there_content" v-for="(item,index) in Icon" :key="index" @click="courseItem">
				<text class="content_icon icon iconfont" :class="item.icon"></text>
				<view class="content_text">{{item.text}}</view>
			</view>
		</view> -->
		<!-- img 广告 -->
				<view class="img_one">
					<img src="../../static/onlineimg.png" alt="" style="width: 100%;">
				</view>
				
			<!-- 限时免费 -->
			<!-- <view class="box_free">
				<h3 style="width: 100%;height:20px;line-height: 20px;align-items: center;display: flex;background-color: red;">限时免费</h3>
				<view class="box">
					<view class="img">
						<img src="../../static/couimg1.png" alt="" style="display: flex;width: 50px;height: 50px;">
					</view>		 -->	
							<!-- <view class="text_jie">
								<text>高淇 教父级Java讲师</text>
								<text>7553人学过</text>
							</view>
							<view style="float:right;display: flex;align-items: center;">
								<text class="bao">马上报名</text>
							</view> -->
					
					
					<!-- <view class="text_san">
						<text>面向对象详解和JVM底层内存分析</text>
							<view class="text_jie">
							<text>高淇 教父级Java讲师</text>
							<text>7553人学过</text>
						</view>
					</view> -->
					
					
				<!-- </view>
			</view> -->
			<!-- 限时免费 -->
				<h3 style="width: 100%;height:40px;line-height: 40px;padding:0px 0px 0px 10px">限时免费</h3>
			
			<view class="free_card_box" v-for="(item,index) in teaList" :key="index">
				<view class="free_card_img">
					<image :src="item.teacher_logo" mode=""></image>
				</view>
				<view class="free_card_txt">
					<view class="free_card_T">{{ item.limitName }}</view>
					<view class="free_card_info">
						<view class="free_card_info_txt">
							<view class="info_txt1">{{ item.teacher_name }}{{ item.teacher_job }}</view>
							<view>{{ item.limitNum }}人学过</view>
						</view>
						<view class="free_card_info_btn" v-if="item.baoming == '马上报名'">{{ item.baoming }}</view>
						<view class="free_card_info_btn free_card_info_btn1" v-else>{{ item.baoming }}</view>
					</view>
				</view>
			</view>
			<!-- 零基础就业班 -->
			<!-- <view class=""> -->
				<h3 style="width: 100%;height:40px;line-height: 40px;padding:0px 0px 0px 10px">零基础就业班</h3>
				<view class="zore_class" v-for="(item,index) in card" :key="index">
					<view class="zore_box">
						<text>11</text>
						<text>{{itme.textT}}</text>
						<img :src="item.icon" alt="" />
						<text>{{item.text}}</text>
						<text>免费试学</text>
					</view>
				</view>
			</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				searchValue: '', // 搜索框的值
				background: ['color1', 'color2', 'color3'],
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500,
				Icon:[],
				teaList:[],
				// card:[
				// 	{
				// 		textT: "JavaEE就业班",
				// 		text: "编程霸主，就业率高",
				// 		icon: "icon-java",
				// 		colors: "job_scroll_card6",
				// 		free:"免费试学"
				// 	},
				// 	{
				// 		textT: "Python全栈工程师",
				// 		text: "未来受欢迎的编程语言",
				// 		icon: "icon-icon--",
				// 		colors: "job_scroll_card6",
				// 		free:"免费试学"
				// 	},
				// ]
			}
		},
		onLoad() {
			
		},
		mounted(){
			uni.request({
				url:"http://html5.bjsxt.cn/api/index/nav",
					success: (res) => {
						console.log(res)
						this.Icon = res.data.data
				}
			}),
			uni.request({
				url:"http://html5.bjsxt.cn/api/index/specific?userid=2162",
				success:(res) =>{
					this.teaList = res.data.data
				}
			})
		},
		methods: {
			 changeIndicatorDots(e) {
				this.indicatorDots = !this.indicatorDots
			},
			changeAutoplay(e) {
				this.autoplay = !this.autoplay
			},
			intervalChange(e) {
				this.interval = e.target.value
			},
			durationChange(e) {
				this.duration = e.target.value
			},
			courseItem(id,course){
				uni.navigateTo({
					url:"/pages/couser/courseIntroduce/courseIntroduce?id=" + id +"&course="+course
				})
			}
			
		}
	}
</script>

<style lang="scss" scoped>
	@import "@/common/font/iconfont.css";
	// .background{
	// 	width:100%;
	// 	height: 120px;
	// 	background-color:#00dc6c;
	// 	color:#fff;
	// 	font-size:20px;
	// 	padding:20px 0px 0px 0px;
	// 	display: flex;
	// 	justify-content: center;
	// }
	.search{
	  position: relative;
	  display: flex;
	  align-items: center;
	  justify-content: space-around;
	  padding: 0px 0px 0px 15px;
	  background-color: #fffbff;
	}
	.search-input{
		width: 100%; /* 让输入框充满父容器 */
		padding:10px;
		border: 1px solid #ccc;
		
		// background-color: #ccc;
		border-radius: 50px;
		padding-left: 50px; /* 设置左侧空间给图标留出位置 */
		box-sizing: border-box; /* 让padding不撑大宽度 */
		height: 40px;
	}
	.search-icon {
	  position: absolute;
	  left: 30px;
	  top: 55%;
	  transform: translateY(-50%);
	  cursor: pointer;	  
	}
	.Ma{
		// position: absolute;
	}
	.uni-margin-wrap{
		padding:10px;
		.swiper-item img{
			width: 100%;
			height:100%;
		}
	}
	.box_there{
		display: flex;
		// 盒子模型不撑开容器本身大小
		box-sizing: border-box;
		flex-direction: row;
		flex-wrap: wrap;
		padding: 15px 10px;
		.box_there_content{
			width: 20%;
			flex-direction: row;
			flex-wrap: wrap;
			text-align: center;
			margin-bottom: 15px;
			.content_icon {
				font-size: 30px;
			}
			.icon-java {
				color: #2a83fe;
			}

			.icon-weifuwu {
				color: #fd3761;
			}

			.icon-zuzhijiagou {
				color: #2b91e2;
			}

			.icon-dashuju {
				color: #2a83fe;
			}

			.icon-h {
				color: #00b478;
			}

			.icon-icon-- {
				color: #fd6012;
			}

			.icon-rengongzhineng {
				color: #fe391f;
			}

			.icon-ruanjianceshi {
				color: #00b478;
			}

			.icon-huatong {
				color: #fea917;
			}

			.icon-bianchengshibaobiao_icon {
				color: #2a83fe;
			}

			.icon-jianmo {
				color: #00b478;
			}

			.icon-chuangye {
				color: #fe391f;
			}

			.content_text {
				width: 100%;
				font-size: 13px;
				margin-top: 10px;
				white-space: nowrap;
				text-overflow: ellipsis;
				overflow: hidden;
			}	
		}
	}
	
	
	// .img_one{
	// 		// width: 100%;
	// 		// height:100px;
	// 		padding:10px;
	// 	}
	// 	.box_free{
	// 		padding:10px;
	// 		.box{
	// 			width: 100%;
	// 			height: 100px;
	// 			background-color: skyblue;
	// 			border-radius: 10px;
	// 			display: flex;
	// 			align-items: center;	
	// 		}
	// 		.text_san{
	// 			display: flex;
	// 			flex-direction: column;
	// 			font-size: 20px;
	// 			justify-content: space-between;
	// 			align-items: center;
	// 		}
				/* 呃呃 就第一个text是保持在上面的不动   小的text 和 报名 jucspace-b -a  可能使用float */
		// 	.text_jie{
		// 		display: flex;
		// 		flex-direction: column;
		// 		font-size: 15px;
		// 		align-items: center;
		// 	}
		// 	.bao{
		// 		border-radius: 50px;
		// 		color:#fff;
		// 		background-color: green;
		// 		padding:5px;
		// 		width: 100px;
		// 		height: 20px;
		// 		float: right;
		// 		display: flex;
		// 		justify-content: center;
		// 	}
		// }
		
		
		.free_card_box{
				display: flex;
				padding: 10px 0;
				margin: 10px;
				border-radius: 10px;
				box-shadow: 0 0  5px 1px rgba($color: #000000, $alpha: 0.1);
				box-sizing: border-box;
				align-items: center;
				margin-bottom: 15px;
				background-color: #fff;
				.free_card_img{
					flex-shrink: 0;
					width: 91rpx;
					height: 91rpx;
					border-radius: 100%;
					margin: 0 15px;
					image{
						width: 100%;
						height: 100%;
						border-radius: 100%;
					}
				}
				.free_card_txt{
					width: 100%;
					display: flex;
					box-sizing: border-box;
					flex-direction: column;
					padding: 0 15px 0 0;
					.free_card_T{
						font-size: 16px;
						white-space: nowrap;
						text-overflow: ellipsis;
						overflow: hidden;
						margin: 10px 0;
					}
					.free_card_info{
						width: 100%;
						display: flex;
						box-sizing: border-box;
						flex-flow: row nowrap;
						justify-content: space-between;
						.free_card_info_txt{
							width: 60%;
							overflow: hidden;
							font-size: 16px;
							color: #666;
							.info_txt1{
								height: 20px;
								font-size:14px;
								overflow: hidden;
							}
						}
						.free_card_info_btn{
							width: 100px;
							height: 34px;
							text-align: center;
							line-height: 34px;
							border-radius: 34px;
							background-color: #00dc6c;
							color: #fff;
							font-size: 16px;
							margin-top: 10px;
						}
						.free_card_info_btn1{
							background-color: #00dc6c;
							/* #ddd */
						}
					}
				}
			}
			
			
			.zore_class{
				width: 100%;
				height: 100vh;
				background-color:red;
				.zore_box{
					background-color: skyblue;
					border-radius: 10px;
				}
			}
</style>
