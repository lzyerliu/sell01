<template>
	<div class="line-title">
		<div class="line" :style="lineColor"></div>
		<div class="text">{{textTitle}}</div>
		<div class="line" :style="lineColor"></div>
	</div>
</template>

<script type="ecmascript-6">
	export default {
		props: {
			textTitle: {
				type: String
			},
			lineColor: {
				type: String
			}
		}
	};
</script>

<style lang="stylus" rel="stylesheet/stylus">
	.line-title
		display: flex
		.line
			flex: 1
			position: relative
			top: -6px
		.text
			padding: 0 12px
			font-size: 14px
			font-weight: 700
</style>
