<template>
	<div>
		<action v-for="(action, a) in actions" :key="a" :action="action" :logs="[]" :leeks="leeks" :report="report" :display-logs="displayLogs && (displayAlliesLogs || action.me)" class="action" :class="{turn: action.params[0] === ActionType.NEW_TURN || action.params[0] === ActionType.START_FIGHT}" />
	</div>
</template>

<script lang="ts">
	import ActionElement from '@/component/report/action.vue'
	import { Action, ActionType } from '@/model/action'
	import { Report } from '@/model/fight'
	import { Component, Prop, Vue } from 'vue-property-decorator'

	@Component({ name: "actions", components: { action: ActionElement } })
	export default class ActionsElement extends Vue {
		@Prop({required: true}) report!: Report
		@Prop({required: true}) actions!: number[][]
		@Prop({required: true}) leeks!: {[key: number]: any}
		@Prop({required: true}) displayLogs!: boolean
		@Prop({required: true}) displayAlliesLogs!: boolean

		ActionType = ActionType
	}
</script>

<style lang="scss" scoped>
	.turn {
		position: sticky;
		top: 0;
		background: #f2f2f2;
		padding: 7px 0;
		margin: 0;
	}
</style>
