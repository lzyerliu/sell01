<template>
	<div class="cart-control">
	<transition name="move">
	<div class="cart-decrease" v-show="food.count>0" @click.stop.prevent="decreaseCart">
		<i class="inner icon-remove_circle_outline"></i>
	</div>
	</transition>
		<div class="cart-count" v-show="food.count>0">{{food.count}}</div>
		<div class="cart-add icon-add_circle" @click.stop.prevent="addCart"></div>
	</div>
</template>

<script type="ecmascript-6">
	import Vue from 'vue';
	export default {
		props: {
			food: {
				type: Object
			}
		},
		methods: {
			addCart(event) {
				if (!event._constructed) {
					return;
				}
				if (!this.food.count) {
					Vue.set(this.food, 'count', 1);
				} else {
					this.food.count++;
				}
				this.$emit('cart-add', event.target);
			},
			decreaseCart() {
				if (!event._constructed) {
					return;
				}
				if (this.food.count) {
					this.food.count--;
				}
			}
		}
	};
</script>

<style lang="stylus" rel="stylesheet/stylus">
	.cart-control
		font-size: 0
		.cart-decrease
			display: inline-block
			padding: 6px
			&.move-enter-active, &.move-leave-active
				transition: all .3s linear
			&.move-enter, &.move-leave-to
				opacity: 0
				transform: translate3d(24px, 0, 0)
			.inner
				display: inline-block
				line-height: 24px
				font-size: 24px
				color: rgb(0, 160, 220)
		.cart-count
			display: inline-block
			vertical-align: top
			// width: 6px
			line-height: 24px
			padding-top: 6px
			font-size: 10px
			text-align: center
			color: rgb(147, 153, 159)
		.cart-add
			display: inline-block
			padding: 6px
			line-height: 24px
			font-size: 24px
			color: rgb(0, 160, 220)
</style>
