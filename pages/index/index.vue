<template>
	<view class="index-content">
		<view class="index-item">
			<view class="index-item-header">
				<image src="../../static/home_fzks@2x.png" mode="aspectFit" class="index-item-header-icon"></image>
				<view class="index-item-header-title">仿真考试</view>
				<view class="index-item-header-right-title">练习记录</view>
			</view>
			<view class="index-exam-category">
				<view class="index-exam-category-item" @click="indexExamCategory('阶段测试')">
					<image src="../../static/home_jdcs@2x.png" mode="aspectFit" class="index-exam-category-item-image"></image>
					<text class="index-exam-category-item-title">阶段测试</text>
				</view>
				<view class="index-exam-category-item" @click="indexExamCategory('专项训练')">
					<image src="../../static/home_zxxl@2x.png" mode="aspectFit" class="index-exam-category-item-image"></image>
					<text class="index-exam-category-item-title">专项训练</text>
				</view>
				<view class="index-exam-category-item" @click="indexExamCategory('同步训练')">
					<image src="../../static/home_tbxl@2x.png" mode="aspectFit" class="index-exam-category-item-image"></image>
					<text class="index-exam-category-item-title">同步训练</text>
				</view>
			</view>
		</view>
		<view class="index-item">
			<view class="index-item-header">
				<image src="../../static/home_wdkc@2x.png" mode="aspectFit" class="index-item-header-icon"></image>
				<view class="index-item-header-title">我的课程</view>
				<view class="index-item-header-right-title">所有课程</view>
			</view>
			<view class="index-course">
				<view v-for="(item) in course" :key="item" class="index-course-item">
					<image src="../../static/home_wdkc@2x.png" mode="aspectFit" class="index-course-item-image"></image>
					<view class="index-course-item-text-area">
						<text class="index-course-item-text-area-title">北师大版八年级下册</text>
						<view class="index-course-item-text-area-sub">
							<view class="index-course-item-text-sub-progress">已完成50%</view>
							<view class="index-course-item-text-sub-avg">平均分 44分</view>
						</view>
					</view>
					<view class="index-course-item-btn">去练习</view>
				</view>
			</view>
		</view>
		<view class="index-item">
			<view class="index-item-header">
				<image src="../../static/home_zxsj@2x.png" mode="aspectFit" class="index-item-header-icon"></image>
				<view class="index-item-header-title">最新试卷</view>
				<!-- <view class="index-item-header-right-title"></view> -->
			</view>
			<view class="index-exam">
				<view v-for="(item) in exam" :key="item" class="index-exam-item">
					<view class="index-exam-item-left"></view>
					<view class="index-exam-item-title">深圳市2019中考人机对话模拟卷2</view>
					<view class="index-exam-item-right">
						<view class="index-exam-item-right-score">36.9</view>
						<view class="index-exam-item-right-msg">最高成绩</view>
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
				course: ['', ''],
				exam: ['', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '']
			}
		},
		onLoad() {

		},
		methods: {
			indexExamCategory:function (event) {
				console.log(event)
				uni.navigateTo({
					url:'exam_list/exam_list?navTitle='+event
				})
			}
		}
	}
</script>

<style>
	@import url("index.css");
</style>
