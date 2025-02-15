<template lang="html">
	<svg :viewBox="'0 0 ' + width + ' ' + height" :width="width * scale" :height="height * scale" v-on="on">
		<g :class="{invert}">
			<image v-if="leekImage" :x="leekX" :y="leekY" :width="leekWidth" :height="leekHeight" :xlink:href="'/image/' + leekImage" />
			<image v-if="hasHat && hatImage" :x="hatX" :y="hatY" :width="hatWidth" :height="hatHeight" :xlink:href="'/image/' + hatImage" />

			<g v-if="weapon || leek.fish" :transform="'translate(' + (leekWidth / 2 + weaponCX) + ',' + (leekY + leekHeight - weaponCY) + ')'">
				<g :transform="'scale(' + weaponScale + ')'">
					<g :transform="'rotate(' + weaponAngle + ')'" transform-box="fill-box">
						<g :transform="'translate(' + weaponX + ',' + weaponY + ')'">
							<image :xlink:href="weaponImage" :width="weaponWidth" :height="weaponHeight" />
							<image :xlink:href="handImage" :width="handSize" :height="handSize" :x="hand1.x - handSize / 2" :y="hand1.y - handSize / 2" />
							<image :xlink:href="handImage" :width="handSize" :height="handSize" :x="hand2.x - handSize / 2" :y="hand2.y - handSize / 2" />
						</g>
					</g>
				</g>
			</g>
		</g>
		<!-- <circle :cx="leekWidth / 2 + weaponCX" :cy="leekY + leekHeight - weaponCY" r="5" fill="red" /> -->
	</svg>
</template>

<script lang="ts">
	import { HatTemplate } from '@/model/hat'
	import { Leek } from '@/model/leek'
	import { LeekWars } from '@/model/leekwars'
	import { FishData, WeaponsData } from '@/model/weapon'
	import { Component, Prop, Vue, Watch } from 'vue-property-decorator'

	@Component({})
	export default class LeekImage extends Vue {
		@Prop({required: true}) leek!: Leek
		@Prop({required: true}) scale!: number
		@Prop() on!: any
		@Prop() invert!: boolean
		@Prop() ai!: number

		botHats = [ null, 8, 12, 13 ]
		randomAngle: number = 0

		created() {
			// setInterval(() => this.randomAngle = Math.random() * Math.PI / 2 - Math.PI / 4, 500)
		}

		get leekImage(): string {
			return 'leek/leek' + this.appearance + '_front_' + LeekWars.getLeekSkinName(this.leek.skin) + '.png'
		}
		get hat() {
			let hat = this.leek.hat
			if (!hat && (!this.leek.real || this.leek.bot)) {
				hat = this.botHats[-this.ai! as number - 1]
			}
			return hat
		}
		get hatImage(): string {
			if (this.hat) {
				const hatName = LeekWars.hats[LeekWars.hatTemplates[this.hat].item].name
				return 'hat/' + hatName + '.png'
			}
			return ''
		}
		get hatTemplate(): HatTemplate | null {
			return this.hat ? LeekWars.hats[LeekWars.hatTemplates[this.hat].item] : null
		}
		get hatWidth() { return this.hatTemplate ? this.leekWidth * this.hatTemplate.width : 0 }
		get hatHeight() { return this.hatSize ? this.hatWidth * (this.hatSize.height / this.hatSize.width) : 0 }
		get hasHat(): boolean { return this.hat !== null }
		get leekWidth(): number { return this.leekSize ? this.leekSize.width : 0 }
		get leekHeight(): number { return this.leekSize ? this.leekSize.height : 0 }
		get width(): number {
			let width = Math.max(this.leekWidth, this.hatWidth)
			const weapon_offset = this.weaponCX + (this.weaponData && this.weaponData.white ? (
								this.weaponRight
							) : (
								(Math.cos(this.weaponRadianAngle) * (this.weaponX + this.weaponWidth)
								+ Math.sin(this.weaponRadianAngle) * (-this.weaponY)
								- Math.sin(this.weaponRadianAngle) * (this.weaponTop))
							)) * this.weaponScale
			if (weapon_offset > width / 2) {
				width = width / 2 + weapon_offset
			}
			return width
		}
		get height(): number {
			let height = this.leekHeight + this.offsetTop
			if (this.hat != null && this.hatTemplate) {
				height += Math.max(0, this.hatHeight - this.leekHeight * this.hatTemplate.height)
			}
			if (this.weaponData && this.weaponData.white) {
				height += this.weaponData.bottom
			} else {
				const weapon_offset = Math.sin(this.weaponRadianAngle) * (this.weaponWidth + this.weaponX)
									+ Math.cos(this.weaponRadianAngle) * (this.weaponHeight + this.weaponY)
									- Math.cos(this.weaponRadianAngle) * (this.weaponHeight - this.weaponBottom)
				if (weapon_offset > this.weaponCY) {
					height += weapon_offset - this.weaponCY
				}
			}
			return height
		}
		get offsetTop() {
			return this.weaponData && this.weaponData.white ? Math.max(0,
				this.weaponData.top - this.leekHeight - (this.hat !== null && this.hatTemplate ? Math.max(0, this.hatHeight - this.leekHeight * this.hatTemplate.height) : 0) + this.weaponData.centerZ +
				Math.abs(Math.sin(this.weaponRadianAngle)) * (this.weaponData.width + this.weaponData.x)
			 ) : 0
		}
		get leekX() { return 0 }
		get leekY() { return this.offsetTop + (this.hat !== null && this.hatTemplate ? Math.max(0, this.hatHeight - this.leekHeight * this.hatTemplate.height) : 0) }
		get hatX() { return this.hat !== null ? this.leekWidth / 2 - this.hatWidth / 2 - (this.leekWidth / 25) : 0 }
		get hatY() { return this.offsetTop }

		get weapon() {
			if (typeof this.leek.weapon === 'number') {
				return this.leek.weapon
			}
			return this.leek.weapon ? ((this.leek.weapon as any).id as number) : 0
		}
		get weaponTemplate() { return this.weapon ? LeekWars.items[this.weapon].params : null }
		get weaponScale() { return 1.0 }
		get weaponData() {
			if (this.leek.fish) {
				return FishData
			}
			return this.weaponTemplate ? WeaponsData[this.weaponTemplate] : null
		}
		get weaponRadianAngle() { return (this.weaponData && this.weaponData.white) ? -Math.PI / 2.7 : Math.PI / 7 + this.randomAngle }
		get weaponAngle() { return this.weaponRadianAngle * (180 / Math.PI) }
		get weaponImage() {
			if (this.leek.fish) {
				return '/image/weapon/fish.png'
			}
			return '/image/' + LeekWars.items[this.weapon].name.replace('_', '/') + '.png' }
		get weaponWidth() { return this.weaponData ? this.weaponData.width : 0 }
		get weaponHeight() { return this.weaponData ? this.weaponData.height : 0 }
		get weaponCX() { return this.weaponData ? this.weaponData.centerX : 0 }
		get weaponCY() { return this.weaponData ? this.weaponData.centerZ : 0 }
		get weaponX() { return this.weaponData ? this.weaponData.x : 0 }
		get weaponY() { return this.weaponData ? this.weaponData.z : 0 }
		get weaponBottom() { return this.weaponData ? this.weaponData.bottom : 0 }
		get weaponTop() { return this.weaponData ? this.weaponData.top : 0 }
		get weaponRight() { return this.weaponData && this.weaponData.right ? this.weaponData.right : 0 }
		get hand1() {
			return this.weaponData ? { x: this.weaponData.hand1x, y: this.weaponData.hand1z } : null
		}
		get hand2() {
			return this.weaponData ? { x: this.weaponData.hand2x, y: this.weaponData.hand2z } : null
		}
		get handSize() { return 20 / this.weaponScale }
		get appearance() { return LeekWars.getLeekAppearance(this.leek.level) }
		get leekSize() { return LeekWars.leekSizes[this.appearance] }
		get hatSize() { return this.hat ? LeekWars.hatSizes[this.hat] : null }
		get handImage() {
			return "/image/fight/leek_hand" + (this.leek.skin === 15 ? "_gold" : "") + ".png"
		}
	}
</script>

<style lang="scss" scoped>
	.invert {
		transform: scale(-1, 1);
		transform-origin: center;
	}
</style>