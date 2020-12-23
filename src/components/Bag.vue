<template>
	<div class="box">
		<div class="section_img">
			<img :src="image" />
		</div>
		<div class="section_info">
			<div class="bag_title">
				<h1>{{ product }}</h1>
			</div>
			<div class="bag_color">
				<div
					v-for="(variant, index) in variants"
					:key="variant.variantId"
					class="color_box"
					:style="{ backgroundColor: variant.variantColor }"
					@mouseover="updateProduct(index)"
				></div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: "Bag",
	data() {
		return {
			product: "bag",
			selectedVariant: 0,
			variants: [
				{
					variantId: 2234,
					variantColor: "red",
					variantImage: require("@/assets/b1.png"),
				},
				{
					variantId: 2235,
					variantColor: "pink",
					variantImage: require("@/assets/b2.png"),
				},
				{
					variantId: 2236,
					variantColor: "blue",
					variantImage: require("@/assets/b3.png"),
				},
			],
		};
	},
	methods: {
		updateProduct: function (index) {
			this.selectedVariant = index;
		},
	},
	computed: {
		image() {
			return this.variants[this.selectedVariant].variantImage;
		},
	},
};
</script>

<style>
.box {
	display: flex;
	flex-direction: row;
}
.section_info {
	display: flex;
	flex-direction: column;
	width: 50%;
	font-weight: 700;
}
.section_img {
	display: flex;
	width: 50%;
}
.bag_color {
	display: flex;
	flex-direction: column;
	justify-content: flex-end;
	align-items: flex-start;
	height: 70%;
}
.bag_title {
	display: flex;
	justify-content: center;
}
.color_box {
	width: 40px;
	height: 40px;
	margin-top: 10px;
}
</style>