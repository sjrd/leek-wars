<template lang="html">
	<span class="talent" v-on="on" @click.stop="LeekWars.goToRanking(category, 'talent', id)">
		<div v-ripple class="icon">
			<img src="/image/talent.png">
		</div>
		<div v-ripple class="value">{{ talent | number }}</div>
	</span>
</template>

<script lang="ts">
	import { Component, Prop, Vue } from 'vue-property-decorator'
	@Component({ name: "talent" })
	export default class Talent extends Vue {
		@Prop() talent!: number
		@Prop() id!: number
		@Prop() category!: string
		@Prop() on!: any
	}
</script>

<style lang="scss" scoped>
	span {
		display: inline-flex;
		align-items: center;
		cursor: pointer;
	}
	.icon {
		z-index: 2;
		display: inline-block;
		width: 34px;
		height: 34px;
		padding: 5px;
		padding-top: 4px;
		padding-bottom: 6px;
		border-radius: 50%;
		background: white;
		box-shadow: 0px 2px 1px -1px rgba(0,0,0,0.2), 0px 1px 1px 0px rgba(0,0,0,0.14), 0px 1px 3px 0px rgba(0,0,0,0.12);
	}
	img {
		width: 24px;
		height: 24px;
	}
	.value {
		display: inline-block;
		margin-left: -8px;
		background: white;
		font-size: 18px;
		padding: 3px 10px;
		padding-left: 14px;
		font-weight: 500;
		box-shadow: 0px 2px 1px -1px rgba(0,0,0,0.2), 0px 1px 1px 0px rgba(0,0,0,0.14), 0px 1px 3px 0px rgba(0,0,0,0.12);
		border-top-right-radius: 14px;
		border-bottom-right-radius: 14px;
	}
</style>