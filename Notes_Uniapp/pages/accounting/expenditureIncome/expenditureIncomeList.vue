<template>
	<view >
		<cu-custom class="cubar" :bgColor="NavBarColor" :isBack="true" backRouterName="index">
		   <block slot="content">支出/录入</block>
		</cu-custom>
		<view class="button-container">
			<view class="box">
				<view class="button-container-box" style="border-radius: 15rpx 0 0 15rpx;" :class="{ active: isExpenditure }" @click="toggleExpenditureIncome(true)">
					<view class="p" >支出</view>
	<!-- 				<button :class="{ active: isExpenditure }" @click="toggleExpenditureIncome(true)">支出</button>
					<button :class="{ active: !isExpenditure }" @click="toggleExpenditureIncome(false)">收入</button> -->
				</view>
				<view class="button-container-box" style="border-radius: 0 15rpx 15rpx 0;" :class="{ active: !isExpenditure }" @click="toggleExpenditureIncome(false)">
					<view class="p" >收入</view>
				</view>
			</view>
		</view>
		<view class="content">
			<!-- 根据 isExpenditure 的值来显示不同的内容 -->
			<view v-if="isExpenditure" style="background: red;">这里是支出的内容</view>
			<view v-else style="background: blue;">这里是收入的内容</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "expenditureIncomeList",
		data() {
			return {
				isExpenditure: true,
			};
		},
		methods: {
		    toggleExpenditureIncome(isExpenditure) {
		      this.isExpenditure = isExpenditure;
		    },
		},
	}
</script>

<style lang="scss" scoped>
	// page {
	// 	background: red;
	// }
	.button-container {
	  display: flex;
	  justify-content: space-around; /* 调整按钮之间的间距 */
	  align-items: center; /* 居中按钮在容器中 */
	  padding: 10px;
	  // background-color: #d9f4f5; /* 背景颜色 */
	}
	.box {
		display: flex;
	}
	.button-container-box {
		width: 250rpx;
		padding: 15rpx 50rpx;
		border: 1px #56526f solid;
		flex: 2;
	}
	.p {
		text-align: center;
		font-size: 15px;
	}
	.button-container-box.active {
		background: #3f3c51;
		color: white;
	}
	// .button-container button {
	//   padding: 0px 36px; /* 调整按钮内边距 */
	//   border: none;
	//   background-color: transparent; /* 去除默认的背景颜色 */
	//   cursor: pointer;
	//   font-size: 14px; /* 调整字体大小 */
	// }
	
	// .button-container button.active {
	//   background-color: linear-gradient(to right, red, yellow);
	//   color: white;
	//   border-radius: 4px; /* 添加圆角效果 */
	// }
	
	.content {
	  padding: 20px;
	  text-align: center;
	}
</style>
