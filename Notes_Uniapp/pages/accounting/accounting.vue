<template>
	<view class="template">
		<cu-custom class="cubar" :bgColor="NavBarColor" :isBack="true" backRouterName="index">
		   <block slot="content">支出</block>
		</cu-custom>
		<view class="expenditure">
			<view class="expenditure-item" v-for="(item, index) in items" :key="index">
			    <view class="expenditure-box">
					<image :src="itemToImage[item]" class="box-image" @click="settlement(item)"></image>
				</view>
			    <view class="box-content">{{ item }}</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "accounting",
		data() {
			return {
				itemToImage: {
					'餐饮': '../../static/img/classify_eat.png',
					'出行': '../../static/img/classify_traffic.png',
					'购物': '../../static/img/classify_shop.png',
					'日用': '../../static/img/classify_dailyuse.png',
						
					'娱乐': '../../static/img/classify_game.png',
					'零食': '../../static/img/classify_snack.png',
					'水果': '../../static/img/classify_fruit.png',
					'烟酒': '../../static/img/classify_smoke.png',
						
					'水电': '../../static/img/classify_waterpower.png',
					'宠物': '../../static/img/classify_pet.png',
					'就医': '../../static/img/classify_doctor.png',
					'运动': '../../static/img/classify_sport.png',
						
					'衣物': '../../static/img/classify_cloth.png',
					'教育': '../../static/img/classify_edu.png',
					'美妆': '../../static/img/classify_face.png',
					'育婴': '../../static/img/classify_baby.png',
				},
				items: ['餐饮', '出行', '购物', '日用', '娱乐', '零食', '水果', '烟酒', '水电', '宠物', '就医', '运动', '衣物', '教育', '美妆', '育婴'],
			};
		},
		methods: {
			// 跳转到支出收入页面
			settlement(item) {
				var itemss = item
				uni.navigateTo({
					url: `/pages/accounting/expenditureIncome/expenditureIncomeList?name=${itemss}`
				})
			},
		}
	}
</script>

<style lang="scss" scoped>
	.template {
		// background: #fafafa;
	}
	.expenditure {
		display: grid;
	    grid-template-columns: repeat(auto-fill, minmax(calc(25% - 10px), 1fr));
	    gap: 10px;
	}
	
	.expenditure-item {
		text-align: center;
	    padding: 10px;
		margin: 5px;
	}
	
	.expenditure-box {
	  width: 45px;
	  height: 45px;
	  border-radius: 50%;
	  
	  display: flex;
	  align-items: center;
	  justify-content: center;
	  margin: 0 auto;
	}
	.box-image {
	  width: 100%;
	  height: 100%;
	  object-fit: cover;
	}
	.box-content {
	  text-align: center;
	  margin-top: 10px;
	}
</style>
