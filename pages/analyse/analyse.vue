<template>
	<view class="analyse-view">
		<view class="analyse-header">
			<text class="analyse-header-title">本周学习平均成绩</text>
			<canvas class="analyse-header-canvas" canvas-id="headerCanvas">
				<view class="analyse-header-canvas-content">
					<canvas class="analyse-header-allow-canvas" canvas-id="allowCanvas"></canvas>
					<text class="analyse-header-canvas-score">78分</text>
					<view class="analyse-header-canvas-score-line"></view>
					<text class="analyse-header-canvas-score-analyse">比上周提升了25%</text>
				</view>
			</canvas>
			<view class="analyse-header-three-score">
				<view class="analyse-header-three-score-practice">
					<text class="analyse-header-three-score-title">同步练习</text>
					<text class="analyse-header-three-score-score">82</text>
				</view>
				<view class="analyse-header-three-score-line"></view>
				<view class="analyse-header-three-score-practice">
					<text class="analyse-header-three-score-title">仿真考试</text>
					<text class="analyse-header-three-score-score">34</text>
				</view>
				<view class="analyse-header-three-score-line"></view>
				<view class="analyse-header-three-score-practice">
					<text class="analyse-header-three-score-title">作业</text>
					<text class="analyse-header-three-score-score">95</text>
				</view>
			</view>
		</view>
		<view class="analyse-content">
			<view class="analyse-item" @click="abilyty">
				<image src="../../static/wodenengli@2x.png" mode="aspectFit" class="analyse-item-icon"></image>
				<text class="analyse-item-title">我的能力</text>
				<image src="../../static/nenglidiwen@2x.png" mode="aspectFit" class="analyse-item-bgicon"></image>
			</view>
			<view class="analyse-item" @click="examAnalyse">
				<image src="../../static/chengjitongji@2x.png" mode="aspectFit" class="analyse-item-icon"></image>
				<text class="analyse-item-title">考试成绩统计</text>
				<image src="../../static/nenglidiwen@2x.png" mode="aspectFit" class="analyse-item-bgicon"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		onReady: function(e) {
			var context = uni.createCanvasContext('headerCanvas')
			var start = Math.PI * (1 / 2 + 1 / 5);
			var end = Math.PI * (2 + 3 / 10);
			var sub = end - start;
			var scoreEnd = sub * 0.78 + start;
			context.beginPath()
			context.setLineCap('round')
			context.setStrokeStyle("rgba(255, 255, 255, 0.3)")
			context.setLineWidth(5)
			context.arc(
				165 / 2,
				165 / 2,
				160 / 2,
				start,
				end,
				false)
			context.stroke()

			context.beginPath()
			context.setStrokeStyle("rgba(255, 255, 255, 1)")
			context.arc(
				165 / 2,
				165 / 2,
				160 / 2,
				start,
				scoreEnd,
				false)
			context.stroke()
			context.draw()

			var context = uni.createCanvasContext('allowCanvas')
			context.setStrokeStyle("rgba(255, 255, 255, 1)")
			context.beginPath()
			context.setLineWidth(2)
			context.moveTo(0, 4.75)
			context.lineTo(4.75, 0)
			context.lineTo(9.5, 4.75)
			context.moveTo(4.75, 0)
			context.lineTo(4.75, 12.35)
			context.stroke()
			context.draw()
		},

		methods: {
			abilyty() {
				uni.navigateTo({
					url: 'ability/ability'
				})
			},
			examAnalyse() {
				uni.navigateTo({
					url: 'exam_analyse/exam_analyse'
				})
			}
		}
	}
</script>

<style>
	@import url("analyse.css");
</style>
