<template>
	<div>
		<Top title="Add a new bank card"/>
		<Card
			:number="card.number"
			:holder="card.holder"
			:valid="card.valid"
			:vendor="card.vendor"
		/>
		<CardForm
			@cardNumber="receiveCardNumber"
			@cardHolder="receiveCardHolder"
			@cardValid="receiveCardValid"
			@cardVendor="receiveCardVendor"
		/>
	</div>
</template>

<script>
import Top from '@/components/Top'
import Card from '@/components/Card'
import CardForm from '@/components/CardForm'

export default {
	name: 'AddCard',
	components: {
		Top,
		Card,
		CardForm
	},
	data() {
		return {
			card: {
				number: '',
				holder: '',
				valid: '',
			}
		}
	},
	methods: {
		receiveCardNumber(cardNumberValue) {
			this.card.number = cardNumberValue
		},
		receiveCardHolder(cardHolderValue) {
			this.card.holder = cardHolderValue
		},
		receiveCardValid(cardValidValue) {
			this.card.valid = cardValidValue
		},
		receiveCardVendor(cardVendorValue) {
			this.card.vendor = cardVendorValue
		}
	},
}
</script>