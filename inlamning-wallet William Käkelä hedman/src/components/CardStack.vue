<template>
	<div class="card-stack-wrapper">
		<Card
			class="card-stack"
			:style="`top: ${index*2}rem`"
			v-for="(card, index) in cards"
			:key="index"
			:number="card.number"
			:holder="card.holder"
			:valid="card.valid"
			:vendor="card.vendor"
			@clicked="selectCard(card, index)"
		/>
	</div>
</template>

<script>
import Card from '@/components/Card'

export default {
	name: 'CardStack',
	components: {
		Card
	},
	props: {
		cards: Array
	},
	/*created() {
		const jsonCards = localStorage.getItem('cards')
		this.cards = JSON.parse(jsonCards)
	},*/
	
	methods: {
		selectCard(card, index) {
			this.$emit('selectCard', card, index)
		}
	},
}
</script>

<style scoped>
.card-stack-wrapper {
	margin-top: 1rem;
	position: relative;
	height: 300px;
	margin-bottom: 5rem;
}

.card-stack {
	position: absolute;
	padding: 1rem;
	border-radius: 5px;
	left: 0;
	right: 0;
}

</style>