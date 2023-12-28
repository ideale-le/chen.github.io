<template>
	<view>
		<!-- <view class="background">
			<text style="background-color: skyblue;display: flex;justify-content: center;align-content: center;width:100%;height: 30px;">分类页面</text> -->
		<!-- </view> -->
		<!-- 搜索框 -->
		
		<view class="search">
		  <input autoFocus v-model="searchValue" class="search-input" placeholder="19588节开发课程,任你搜" />
		</view>
		  <view class="search-icon">
			<!-- 这里放置左侧搜索图标，你可以使用iconfont或者本地图片 -->
			<!-- 示例使用字体图标 -->
			  <img src="../../static/search.png" alt="" style="width:30px;height:30px;">
		  </view>
		<!-- </view> -->
		<!-- 图片介绍 -->
		<view class="img">
			<img src="../../static/fenbanner.png" alt="" style="width:100%;">
		</view>
		<!-- 详情介绍 -->
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
</template>

<script>
	export default {
		data() {
			return {
				searchValue: '', // 搜索框的值
				class_it:[
					{
						url:"../../static/classimg1.png",
						text_one:"JavaEE高薪就业班",
						text_two:"学习阶段:31 课程节数:3334",
						peopleurl:"../../static/class_img_people.png",
						text_there:"479846人学过",
						text_rado:"咨询课程"
					},
					{
						url:"../../static/classimg2.png",
						text_one:"Python 全系列高手班",
						text_two:"学习阶段:31 课程节数:3334",
						peopleurl:"../../static/class_img_people.png",
						text_there:"479846人学过",
						text_rado:"咨询课程"
					},
					{
						url:"../../static/classimg3.png",
						text_one:"Python 后端班",
						text_two:"学习阶段:31 课程节数:3334",
						peopleurl:"../../static/class_img_people.png",
						text_there:"479846人学过",
						text_rado:"咨询课程"
					},
					{
						url:"../../static/classimg4.png",
						text_one:"Java高级架构/微服务",
						text_two:"学习阶段:31 课程节数:3334",
						peopleurl:"../../static/class_img_people.png",
						text_there:"479846人学过",
						text_rado:"咨询课程"
					},
					{
						url:"../../static/classimg5.png",
						text_one:"互联网P8架构师",
						text_two:"学习阶段:31 课程节数:3334",
						peopleurl:"../../static/class_img_people.png",
						text_there:"479846人学过",
						text_rado:"咨询课程"
					},
					{
						url:"../../static/classimg6.png",
						text_one:"大数据开发工程师",
						text_two:"学习阶段:31 课程节数:3334",	
						peopleurl:"../../static/class_img_people.png",
						text_there:"479846人学过",
						text_rado:"咨询课程"
					},
					{
						url:"../../static/classimg7.png",
						text_one:"Web全栈架构师",
						text_two:"学习阶段:31 课程节数:3334",
						peopleurl:"../../static/class_img_people.png",
						text_there:"479846人学过",
						text_rado:"咨询课程"
					},
					{
						url:"../../static/classimg8.png",
						text_one:"软件测试全系列",
						text_two:"学习阶段:31 课程节数:3334",
						peopleurl:"../../static/class_img_people.png",
						text_there:"479846人学过",
						text_rado:"咨询课程"
					},
					{
						url:"../../static/classimg9.png",
						text_one:"7U演讲培训班",
						text_two:"学习阶段:31 课程节数:3334",
						peopleurl:"../../static/class_img_people.png",
						text_there:"479846人学过",
						text_rado:"咨询课程"
					},
					{
						url:"../../static/classimg10.png",
						text_one:"毕设项目",
						text_two:"学习阶段:31 课程节数:3334",
						peopleurl:"../../static/class_img_people.png",
						text_there:"1846人学过",
						text_rado:"咨询课程"
					},
					
				],
			}
		},
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
		flex-direction: column;
		justify-content: center;
	}
	.search{
		width: 100%;
		// height: 40px;
	  position: relative;
	  top:20px;
	  left:0px;
	  display: flex;
	  align-items: center;
	  justify-content: space-around;
	  padding: 0px 15px 0px 15px;
	  background-color: #fffbff;
	  // background-color: red;
	}
	.search-input{
		width: 100%; /* 让输入s框充满父容器 */
		padding:10px;
		border: 1px solid #ccc;
		// background-color: #ccc;
		border-radius: 50px;
		padding-left: 45px; /* 设置左侧空间给图标留出位置 */
		box-sizing: border-box; /* 让padding不撑大宽度 */
		height: 40px;
	}
	.search-icon {
	  position: absolute;
	  left: 26px;
	  top: 5%;
	  transform: translateY(-50%);
	  cursor: pointer;	
	}
	.img{
		padding:20px 15px 0 15px;
	}
	.box{
		padding:10px 20px 0 20px;
		// width: 100%;
		height: 200vh;
		// background-color: red;
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
			// width: 100%;
				.left_class_img{
				// width: 140px;
				// height: 100px;
				float:left;
				display: flex;	
				
			}
			.right_text{
				width: 100%;
				font-weight: 300px;
				float:right;
				// background-color: yellow;
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
				background-color: green;	
				display: flex;
				justify-content: center;
				line-height: 30px;
				font-size: 13px;
				
			}
		}
		
	}
</style>