<template>
	<view>
		<scroll-view scroll-x="true" class="exam-list-category-scroll-view" @scroll="scroll">
			<view v-for="(item) in category" :key="item" class="exam-list-category" @click="categorySelect(item)">
				<template v-if="item==select">
					<view class="exam-list-category-title exam-list-category-title-s">{{item}}</view>
				</template>
				<template v-else>
					<view class="exam-list-category-title exam-list-category-title-n">{{item}}</view>
				</template>
			</view>
		</scroll-view>
		
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
		<uni-load-more :loadingType="1"></uni-load-more>
	</view>
</template>

<script>
	import uniLoadMore from "@/components/uni-load-more/uni-load-more.vue"
	export default {
		components: {
			uniLoadMore
		},
		data() {
			return {
				loadMoreText: "加载中...",
				showLoadMore: false,
				select: '全部',
				category: ['全部', '中考模拟', '同步测验', '期末', '期中', '期末末末', '期末末末末', '期末末末末末末', '期末末末末末末末末'],
				exam: ['', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '','', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '', '']
			}
		},
		onLoad(options) {
			var navTitle = options.navTitle;
			uni.setNavigationBarTitle({
				title: navTitle
			});
		},
		onReachBottom() {
			console.log("onReachBottom");
			if (this.exam.length > 100000) {
				this.loadMoreText = "没有更多数据了!"
				return;
			}
			this.showLoadMore = true;
			setTimeout(() => {
				this.setDate();
			}, 300);
		},
		onPullDownRefresh() {
			console.log('onPullDownRefresh');
			this.initData();
		},
		methods: {
			categorySelect: function(event) {
				this.select = event;
			},
			initData() {
				setTimeout(() => {
					this.exam = [];
					let data = [];
					for (var i = 0; i < 20; i++) {
						data.push(i)
					}
					this.exam = this.exam.concat(data);
					uni.stopPullDownRefresh();
				}, 300);
			},
			setDate() {
				let data = [];
				for (var i = 0; i < 20; i++) {
					data.push(i)
				}

				this.exam = this.exam.concat(data);
				uni.stopPullDownRefresh();
			}
		}
	}
</script>

<style>
	@import url("exam_list.css");
</style>
