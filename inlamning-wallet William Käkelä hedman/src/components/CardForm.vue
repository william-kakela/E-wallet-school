<template>
	<form @submit.prevent="submitCard">
		<label for="card-number">Card number</label>
		<input type="number" id="card-number" minlength="16" maxlength="16" v-model="card.number" required>

		<label for="card-holder">Card holder name</label>
		<input type="text" id="card-holder" v-model="card.holder" required>

		<div class="info-wrapper">
			<div>
				<label for="card-valid">Valid thru</label>
				<input type="date" id="card-valid" v-model="card.valid" required>
			</div>

			<div>
				<label for="card-ccv">CCV</label>
				<input type="number" id="card-ccv" minlength="3" maxlength="3" v-model="card.ccv" required>
			</div>
		</div>

		<label for="card-vendor">Vendor</label>
		<select id="card-vendor" v-model="card.vendor">
			<option value="">Välj</option>
			<option value="ninja_corp">Ninja Bank</option>
			<option value="evil_corp">Evil Corp</option>
			<option value="bit_coin">Bit Coin</option>
			<option value="block_chain">Block Chain</option>
		</select>

		<div class="button-wrapper">
			<button type="submit">
				Add card
			</button>
		</div>
	</form>
</template>

<script>
export default {
	name: 'CardForm',
	data() {
		return {
			card: {
				number: '',
				holder: '',
				valid: '',
				ccv: '',
				vendor: '',
			}
		}
	},
	watch: {
		'card.number': function (newValue) {
			this.$emit('cardNumber', newValue)
		},
		'card.holder': function (newValue) {
			this.$emit('cardHolder', newValue)
		},
		'card.valid': function (newValue) {
			this.$emit('cardValid', newValue)
		},
		'card.vendor': function (newVendor) {
			this.$emit('cardVendor', newVendor)
		}
	},
	methods: {
		submitCard() {
			const cards = localStorage.getItem('cards') 
			const cardsArray = JSON.parse(cards) 

			cardsArray.push(this.card) 

			const jsonCards = JSON.stringify(cardsArray) 
			localStorage.setItem('cards', jsonCards) 

			this.$router.push('/') 
		}
	},
}
</script>

<style scoped>
form {
	padding: 0 1rem;
}

label {
	display: block;
	color: #777;
	text-transform: uppercase;
	font-size: 0.5rem;
	margin-top: 1rem;
}

input {
	width: 100%;
	border-radius: 5px;
	border: 1px solid black;
	padding: 0.5rem 0;
}

select {
	width: 100%;
	border-radius: 5px;
	border: 1px solid black;
	padding: 0.5rem 0;
}

button {
	margin-top: 2rem;
	width: 100%;
	background-color: #000;
	border: none;
	color: #fff;
	padding: 1rem 0;
	border-radius: 5px;
	text-transform: uppercase;
}

.button-wrapper {
	text-align: center;
}

.info-wrapper {
	display: flex;
	justify-content: space-between;
	align-items: center;
}

</style>