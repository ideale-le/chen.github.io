	<template>
		<view>
			<!-- study center -->
			<view class="background">学习中心</view>
			<!-- 三个板块 -->
				<view class="box_aa">
					<view class="box_twi">
						<view class="study">
							<text>学习进度</text>
							<text>6%</text>
						</view>
						<view class="study_play">
							<text>已开通课程</text>
							<text>622节</text>
						</view>
						<view class="study_class" style="border-right:none;">
							<text>已学习课程</text>
							<text>13622节</text>
						</view>
					</view>
				</view>
				
			<!-- 我的课程 -->
			<view class="my_Class">
				<h3 style=" width: 100%;height:20px;line-height: 20px;align-items: center;display: flex;padding:10px 20px 0 10px;">我的课程</h3>
				<view class="box">
					<view class="box_outside" v-for="(item,index) in class_it" :key="index">
						<view class="box_ww" >
						<!-- <view class="" :class="item.text_rado"></view> -->
						<!-- :class 的含义是 你可以去样式里面设置 如:点击变化不同颜色，字体。点击会发生什么 -->
						<view class="left_class_img">
							<img :src="item.url" alt="" style="width: 160px;height: 90px;">
								
						</view>
						<view class="right_text">
							<text style="font-size: 20px;display: flex;">{{item.text_one}}</text>
							<text style="font-size: 13px;">{{item.text_two}}</text>
							<view style="display: flex;line-height: 30px;align-items: center;justify-content: flex-start;">
								<img :src="item.peopleurl" alt=""  style="width: 25px;height: 25px;"/>
								<text style="font-weight: 200px;font-size: 11px;">{{item.text_there}}</text>
								<text class="ask">{{item.text_rado}}</text>
							</view>
						</view>
						</view>
					</view>
				</view>
			</view>
		</view>
	</template>

	<script>
		export default {
			data() {
				return {
					class_it:[
						{
							url:"../../static/classimg1.png",
							text_one:"JavaEE高薪就业班",
							text_two:"学习阶段:31 课程节数:3334",
							peopleurl:"../../static/class_img_people.png",
							text_there:"479846人学过",
							text_rado:"开始学习"
						},
						{
							url:"../../static/classimg2.png",
							text_one:"Python 全系列高手班",
							text_two:"学习阶段:31 课程节数:3334",
							peopleurl:"../../static/class_img_people.png",
							text_there:"479846人学过",
							text_rado:"开始学习"
						},
						{
							url:"../../static/classimg3.png",
							text_one:"Python 后端班",
							text_two:"学习阶段:31 课程节数:3334",
							peopleurl:"../../static/class_img_people.png",
							text_there:"479846人学过",
							text_rado:"开始学习"
						},
						{
							url:"../../static/classimg4.png",
							text_one:"Java高级架构/微服务",
							text_two:"学习阶段:31 课程节数:3334",
							peopleurl:"../../static/class_img_people.png",
							text_there:"479846人学过",
							text_rado:"开始学习"
						},
						{
							url:"../../static/classimg5.png",
							text_one:"互联网P8架构师",
							text_two:"学习阶段:31 课程节数:3334",
							peopleurl:"../../static/class_img_people.png",
							text_there:"479846人学过",
							text_rado:"开始学习"
						},
						{
							url:"../../static/classimg6.png",
							text_one:"大数据开发工程师",
							text_two:"学习阶段:31 课程节数:3334",	
							peopleurl:"../../static/class_img_people.png",
							text_there:"479846人学过",
							text_rado:"开始学习"
						},
						{
							url:"../../static/classimg7.png",
							text_one:"Web全栈架构师",
							text_two:"学习阶段:31 课程节数:3334",
							peopleurl:"../../static/class_img_people.png",
							text_there:"479846人学过",
							text_rado:"开始学习"
						},
						{
							url:"../../static/classimg8.png",
							text_one:"软件测试全系列",
							text_two:"学习阶段:31 课程节数:3334",
							peopleurl:"../../static/class_img_people.png",
							text_there:"479846人学过",
							text_rado:"开始学习"
						},
						{
							url:"../../static/classimg9.png",
							text_one:"7U演讲培训班",
							text_two:"学习阶段:31 课程节数:3334",
							peopleurl:"../../static/class_img_people.png",
							text_there:"479846人学过",
							text_rado:"开始学习"
						},
						{
							url:"../../static/classimg10.png",
							text_one:"毕设项目",
							text_two:"学习阶段:31 课程节数:3334",
							peopleurl:"../../static/class_img_people.png",
							text_there:"1846人学过",
							text_rado:"开始学习"
						},
						
					],
				}
			}	
		}
	</script>

	<style lang="scss" scoped>
		@media screen and (max-width: 300px) {
		    
		}
		.background{
			width:100%;
			height: 120px;
			background-color:#00dc6c;
			color:#fff;
			font-size:20px;
			padding:20px 0px 0px 0px;
			display: flex;
			justify-content: center;
		}
		.box_aa{
			padding:10px 10px 10px 10px;
			display: flex;
			justify-content: space-around;
			position: relative;
			left:0;
			top:-70px;
			// background-color: red;
		}
		.box_twi{
			background-color: #fffbff;
			width: 100%;
			height: 80px;
			border-radius: 5px;
			display: flex;
			justify-content: space-evenly;
			font-weight: 300px;
			font-size: 20px;
			box-shadow: 10px 10px 10px #ccc;
			padding:10px;
			justify-content: flex-end;  // 让中间的线 对准center
		}
		.study, .study_play,.study_class{
			margin-top: -3px;
			display: flex;
			flex-direction: column;
			// justify-content: space-evenly;
			justify-content: space-between;
			// justify-content: flex-end;
			// justify-content: flex-end;
			align-items: center;
			border-right: 3px solid #f9f4f8;
			padding:10px;	
			color:#121011;
		}
		
		.my_Class{
			position: relative;
			top:-70px;
			left:0px;
		}
		
		.box{
			display: flex;
			padding:10px 20px 0 10px;
			// width: 100%;
			height: 200vh;
			// background-color: red;
			flex-direction: column;
			
			.box_outside{
				width: 100%;
				height: 120px;
				background-color: #fffbff;
				border-radius: 10px;
				display:flex;
				justify-content: space-around;
				flex-direction: column;
				padding:0px 5px 0 5px;
				margin-top: 10px;
				box-shadow: 10px 10px 10px #ccc;
			}
			.box_ww{
				display: flex;
				justify-content: space-between;
				align-items: center;
					.left_class_img{
					// width: 140px;
					// height: 100px;
					float:left;
					display: flex;	
					
				}
				.right_text{
					width: 100%;
					font-weight: 200px;
					float:right;
					// background-color: yellow;
					padding:3px;
					display: flex;
					justify-content: space-between;
					flex-direction: column;
					position: relative;
					top:0px;
					left:5px;
					height: 90px;
				}
				.ask{
					width: 70px;
					height: 30px;
					color:#fff;
					border-radius: 50px;
					background-color: #01dc6a;	
					display: flex;
					justify-content: center;
					line-height: 30px;
					font-size: 13px;
					margin-left: 10px;
				}
			}
		}
	</style>