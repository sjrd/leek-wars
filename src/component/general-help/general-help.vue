<template lang="html">
	<div class="help">
		<div class="page-header page-bar">
			<h1>
				<breadcrumb :items="breadcrumb_items" :raw="true" />
			</h1>
			<div class="tabs">
				<router-link to="/help/tutorial">
					<div class="tab">
						<v-icon>mdi-laptop</v-icon>
						{{ $t('main.tutorial') }}
					</div>
				</router-link>
				<router-link to="/help/documentation">
					<div class="tab">
						<v-icon>mdi-book-open-variant</v-icon>
						{{ $t('main.documentation') }}
					</div>
				</router-link>
			</div>
		</div>
		<panel class="first">
			<div slot="content" class="wrapper">
				<center>
					<img src="/image/signup_illustration.png">
					<br><br>
					<h2>{{ $t('welcome') }}</h2>
					<br>
				</center>

				<i18n tag="p" path="intro">
					<router-link slot="tutorial" to="/help/tutorial">{{ $t('intro_tuto') }}</router-link>
				</i18n>

				<div class="help-menu">
					<a href="#farmer"><div class="item card">{{ $t('farmer') }}</div></a>
					<a href="#habs"><div class="item card">{{ $t('habs') }}</div></a>
					<a href="#leeks"><div class="item card">{{ $t('leeks') }}</div></a>
					<a href="#weapons"><div class="item card">{{ $t('weapons') }}</div></a>
					<a href="#chips"><div class="item card">{{ $t('chips') }}</div></a>
					<a href="#teams"><div class="item card">{{ $t('teams') }}</div></a>
					<a href="#fights"><div class="item card">{{ $t('fights') }}</div></a>
					<a href="#challenges"><div class="item card">{{ $t('challenges') }}</div></a>
					<a href="#tournaments"><div class="item card">{{ $t('tournaments') }}</div></a>
					<a href="#trophies"><div class="item card">{{ $t('trophies') }}</div></a>
					<a href="#editor"><div class="item card">{{ $t('editor') }}</div></a>
				</div>
			</div>
		</panel>

		<panel id="farmer" :title="$t('farmer')">
			<div slot="content" class="wrapper">
				<p>{{ $t('farmer_1') }}</p>

				<p>{{ $t('farmer_2') }}</p>

				<p>{{ $t('farmer_3') }}
					<ul>
						<li>{{ $t('farmer_4') }}</li>
						<li>{{ $t('farmer_5') }}</li>
						<li>{{ $t('farmer_6') }}</li>
						<li>{{ $t('farmer_7') }}</li>
					</ul>
				</p>
			</div>
		</panel>

		<panel id="habs" :title="$t('habs')">
			<div slot="content" class="wrapper">
				<i18n tag="p" path="habs_1">
					<span slot="icon" class="hab"></span>
				</i18n>
			</div>
		</panel>

		<panel id="leeks" :title="$t('leeks')">
			<div slot="content" class="wrapper">
				<!-- intro -->
				<p v-html="$t('leeks_1')"></p>
				<p>{{ $t('leeks_2') }}</p>
				<p>{{ $t('leeks_3') }}</p>
				<p>{{ $t('leeks_4') }}</p>

				<!-- life -->
				<h3>{{ $t('leeks_5') }}</h3>
				<p>{{ $t('leeks_6') }}</p>

				<!-- force -->
				<h3>{{ $t('leeks_11') }}</h3>
				<p>{{ $t('leeks_12') }}</p>
				<div class="formula">{{ $t('leeks_13') }}</div>

				<!-- wisdom -->
				<h3>{{ $t('leeks_7') }}</h3>
				<p>{{ $t('leeks_8') }}</p>
				<div class="formula">{{ $t('leeks_9') }}</div>
				<div class="formula">{{ $t('leeks_10') }}</div>

				<!-- agility -->
				<h3>{{ $t('leeks_14') }}</h3>
				<p>{{ $t('leeks_15') }}</p>
				<div class="formula">{{ $t('leeks_16') }}</div>
				<p>{{ $t('leeks_34') }}</p>
				<div class="formula">{{ $t('leeks_32') }}</div>

				<!-- resistance -->
				<h3>{{ $t('leeks_33') }}</h3>
				<p>{{ $t('leeks_36') }}</p>
				<p>{{ $t('leeks_17') }}</p>
				<div class="formula">{{ $t('leeks_18') }}</div>
				<div class="formula">{{ $t('leeks_19') }}</div>
				<p>{{ $t('leeks_35') }}</p>
				<div class="formula">{{ $t('leeks_21') }}</div>

				<!-- science -->
				<h3>{{ $t('leeks_28') }}</h3>
				<p>{{ $t('leeks_29') }}</p>
				<div class="formula">{{ $t('leeks_37') }}</div>
				<p>{{ $t('leeks_37_1') }}</p>
				<div class="formula">{{ $t('leeks_37_2') }}</div>

				<!-- magic -->
				<h3>{{ $t('leeks_30') }}</h3>
				<p>{{ $t('leeks_31') }}</p>
				<div class="formula">{{ $t('leeks_38') }}</div>
				<div class="formula">{{ $t('leeks_41') }}</div>

				<!-- frequency -->
				<h3>{{ $t('leeks_26') }}</h3>
				<p>{{ $t('leeks_27') }}</p>

				<!-- tp -->
				<h3>{{ $t('leeks_22') }}</h3>
				<p>{{ $t('leeks_23') }}</p>

				<!-- mp -->
				<h3>{{ $t('leeks_24') }}</h3>
				<p>{{ $t('leeks_25') }}</p>
			</div>
		</panel>

		<panel id="weapons" :title="$t('weapons')">
			<div slot="content" class="wrapper">

				<p>{{ $t('weapons_1') }}</p>

				<center>
					<img src="/image/weapon/pistol.png"> &nbsp; &nbsp;
					<img src="/image/weapon/laser.png"> &nbsp; &nbsp;
					<img src="/image/weapon/electrisor.png">
				</center>

				<p>{{ $t('weapons_2') }}</p>
				<p>{{ $t('weapons_3') }}</p>

				<center>
					<img src="/image/help/forgotten_weapon.png"> &nbsp; &nbsp;
				</center>

				<p>{{ $t('weapons_4') }}</p>
				<p>{{ $t('weapons_5') }}</p>
			</div>
		</panel>

		<panel id="chips" :title="$t('chips')">
			<div slot="content" class="wrapper">
				<p>{{ $t('chips_1') }}</p>

				<center>
					<img width="60" src="/image/chip/flash.png"> &nbsp;
					<img width="60" src="/image/chip/cure.png"> &nbsp;
					<img width="60" src="/image/chip/fortress.png"> &nbsp;
					<img width="60" src="/image/chip/doping.png">
				</center>

				<p>{{ $t('chips_2') }}</p>

				<p>{{ $t('chips_3') }}</p>
				<p>{{ $t('chips_4') }}</p>
			</div>
		</panel>

		<panel id="teams" :title="$t('teams')">
			<div slot="content" class="wrapper">
				<p>{{ $t('teams_1') }}</p>

				<p v-html="$t('teams_2')"></p>

				<h3>{{ $t('teams_3') }}</h3>
				<p>{{ $t('teams_4') }}</p>

				<h3>{{ $t('teams_5') }}</h3>
				<p>{{ $t('teams_6') }}</p>
			</div>
		</panel>

		<panel id="fights" :title="$t('fights')">
			<div slot="content" class="wrapper">
				<p>{{ $t('fights_1') }}</p>
				<ul>
					<li>{{ $t('fights_2') }}</li>
					<li>{{ $t('fights_3') }}</li>
					<li>{{ $t('fights_4') }}</li>
					<li>{{ $t('fights_5') }}</li>
				</ul>
				<p v-html="$t('fights_6')"></p>
				<p>{{ $t('fights_7') }}</p>

				<h3>{{ $t('fights_8') }}</h3>
				<p v-html="$t('fights_9')"></p>
				<p>{{ $t('fights_10') }}</p>

				<h3>{{ $t('fights_11') }}</h3>
				<p>{{ $t('fights_12') }}</p>
				<p>{{ $t('fights_13') }}</p>

				<h3>{{ $t('fights_14') }}</h3>
				<p v-html="$t('fights_15')"></p>
				<center>
					<img height="240" src="/image/help/turret.png"> &nbsp;
				</center>
				<p v-html="$t('fights_16')"></p>
				<p v-html="$t('fights_17')"></p>
				<p>{{ $t('fights_18') }}</p>

				<h3>{{ $t('fights_19') }}</h3>
				<p>{{ $t('fights_20') }}</p>
				<p>{{ $t('fights_21') }}</p>
			</div>
		</panel>

		<panel id="challenges" :title="$t('challenges')">
			<div slot="content" class="wrapper">
				<p v-html="$t('challenges_1')"></p>
				<p>{{ $t('challenges_2') }}</p>
			</div>
		</panel>

		<panel id="tournaments" :title="$t('tournaments')">
			<div slot="content" class="wrapper">
				<p>{{ $t('tournaments_1') }}</p>
				<ul>
					<li>{{ $t('tournaments_2') }}</li>
					<li>{{ $t('tournaments_3') }}</li>
					<li>{{ $t('tournaments_13') }}</li>
				</ul>

				<h3>{{ $t('tournaments_4') }}</h3>

				<p>{{ $t('tournaments_5') }}</p>
				<p>{{ $t('tournaments_6') }}</p>

				<h3>{{ $t('tournaments_7') }}</h3>

				<p>{{ $t('tournaments_8') }}</p>
				<p>{{ $t('tournaments_9') }}</p>

				<h3>{{ $t('tournaments_10') }}</h3>

				<p>{{ $t('tournaments_11') }}</p>
				<p>{{ $t('tournaments_12') }}</p>
			</div>
		</panel>

		<panel id="trophies" :title="$t('trophies')">
			<div slot="content" class="wrapper">
				<p>{{ $t('trophies_1') }}</p>
				<p>{{ $t('trophies_2') }}</p>
			</div>
		</panel>

		<panel id="editor" :title="$t('editor')">
			<div slot="content" class="wrapper">
				<p>{{ $t('editor_1') }}</p>
				<p v-html="$t('editor_2')"></p>
				<i18n tag="p" path="editor_3">
					<router-link slot="tutorial" to="/help/tutorial">{{ $t('editor_tuto') }}</router-link>
				</i18n>
			</div>
		</panel>

		<panel>
			<div slot="content" class="wrapper">
				<div class="credits" v-html="$t('credits')"></div>
			</div>
		</panel>
	</div>
</template>

<script lang="ts">
	import { mixins } from '@/model/i18n'
	import { LeekWars } from '@/model/leekwars'
	import { Component, Vue } from 'vue-property-decorator'
	import Breadcrumb from '../forum/breadcrumb.vue'

	@Component({ name: "general_help", i18n: {}, mixins: [...mixins], components: { Breadcrumb } })
	export default class GeneralHelp extends Vue {
		created() {
			LeekWars.setTitle(this.$t('title'))
			this.$root.$emit('loaded')
		}

		get breadcrumb_items() {
			return [
				{name: this.$t('main.help'), link: '/help'},
				{name: this.$t('title'), link: '/help/general'}
			]
		}
	}
</script>

<style lang="scss" scoped>
	h3 {
		margin-top: 10px;
		margin-bottom: 5px;
	}
	#app.app h3 {
		margin-left: 0;
	}
	p {
		margin-bottom: 10px;
		margin-left: 20px;
		margin-right: 20px;
		text-align: justify;
		font-size: 16px;
	}
	#app.app p {
		margin-left: 10px;
		margin-right: 10px;
		margin-top: 10px;
	}
	ul {
		font-size: 16px;
	}
	.panel a {
		color: #5fad1b;
	}
	.help-menu {
		margin-top: 20px;
		text-align: center;
	}
	.help-menu .item {
		display: inline-block;
		vertical-align: bottom;
		margin: 6px;
		padding: 10px;
		text-align: center;
		width: 130px;
		border: 2px solid #0000;
		font-weight: 300;
		color: #555;
		font-size: 18px;
		cursor: pointer;
	}
	.help-menu .item:hover {
		border: 2px solid #5fad1b;
		color: #5fad1b;
	}
	.formula {
		background: white;
		font-family: monospace;
		padding: 8px 10px;
		margin: 5px 15px;
		border-radius: 3px;
		display: block;
		border-bottom: 2px solid #ddd;
	}
	#app.app .formula {
		margin: 5px 0;
	}
	.credits {
		text-align: right;
		color: #999;
		font-style: italic;
	}
	.help .panel {
		background: #e3e3e3;
		padding: 0;
	}
	.panel .wrapper {
		max-width: 800px;
		margin: 0 auto;
		background: #f2f2f2;
		padding: 15px;
	}
	#app.app .panel .wrapper {
		padding: 8px 0;
	}
</style>