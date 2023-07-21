<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<navigator url="../detail/detail">
				<u-button>文章详情</u-button>
			</navigator>
			<navigator url="../honestySchool/honestySchool">
				<u-button>文章列表</u-button>
			</navigator>
			<navigator url="../contractList/contractList">
				<u-button>博士合同</u-button>
			</navigator>
		</view>
	</view>
</template>

<script setup>
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
