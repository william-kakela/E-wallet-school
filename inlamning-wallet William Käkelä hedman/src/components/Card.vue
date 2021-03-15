<template>
	<div class="card" :class="cardColor(vendor)" @click="$emit('clicked')">
		<div class="badge-wrapper">
			<img :src="require(`../assets/${chipType(vendor)}`)" alt="chip">
			<img :src="require(`../assets/${vendorType(vendor)}`)" alt="chip">
		</div>

		<div class="card-number">{{ number }}</div>

		<div class="info-wrapper">
			<div>
				<div class="info">Cardholder name</div>
				<div>{{ holder }}</div>
			</div>
			<div>
				<div class="info text-right">Valid thru</div>
				<div>{{ valid }}</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Card',
	props: {
		number: {
			type: String,
			default: 'XXXX XXXX XXXX XXXX'
		},
		holder: {
			type: String,
			default: 'FIRSTNAME LASTNAME'
		},
		valid: {
			type: String,
			default: 'MM/YY'
		},
		vendor: {
			type: String,
			default: 'vendor-bitcoin.svg'
		},
	},
	computed: {
	cardColor() {
    return (vendor) => {
        if (vendor === 'bit_coin') {
            return 'bit_coin'
        }
        else if (vendor === 'ninja_corp') {
            return 'ninja_corp'
        }
        else if (vendor === 'block_chain') {
            return 'block_chain'
        }
        else if (vendor === 'evil_corp') {
            return 'evil_corp'
        }
        else {
            return ''
        }
    }
},
		vendorType() {
    return (vendor) => {
        if (vendor === 'bit_coin') {
            return 'vendor-bitcoin.svg'
        }
        else if (vendor === 'ninja_corp') {
            return 'vendor-ninja.svg'
        }
        else if (vendor === 'block_chain') {
            return 'vendor-blockchain.svg'
        }
        else if (vendor === 'evil_corp') {
            return 'vendor-evil.svg'
        }
        else {
            return 'vendor-bitcoin.svg'
        }
    }
},
	chipType() {
    return (vendor) => {
        if (vendor === 'bit_coin') {
            return 'chip-dark.svg'
        }
        else if (vendor === 'ninja_corp') {
            return 'chip-light.svg'
        }
        else if (vendor === 'block_chain') {
            return 'chip-dark.svg'
        }
        else if (vendor === 'evil_corp') {
            return 'chip-dark.svg'
        }
        else {
            return 'chip-dark.svg'
        }
	}
	}
	}
}

</script>

<style scoped>
.card {
	border-radius: 5px;
	padding: 1rem;
	margin: 1rem 1rem 0 1rem;
	background-color: #D0D0D0;
	color: #FFFFFF;
	border: 2px solid #333333;
}

.bit_coin {
	background-color: #FFAE34;
	color: #FFFFFF;
	border: 2px solid #333333;
}

.ninja_corp {
	background-color: #000000;
	color: #FFFFFF;
	border: 2px solid #333333;
}

.block_chain {
	background-color: #8B58F9;
	color: #FFFFFF;
	border: 2px solid #333333;
}

.evil_corp {
	background-color: #F33355;
	color: #FFFFFF;
	border: 2px solid #333333;
}

.badge-wrapper {
	display: flex;
	justify-content: space-between;
	align-items: flex-start;
}

.card-number {
	text-align: center;
	font-size: 2.3rem;
	margin-top: 1rem;
}

.info-wrapper {
	margin-top: 1rem;
	display: flex;
	justify-content: space-between;
	align-items: center;
}

.info {
	color: #FFFFFF;
	text-transform: uppercase;
	font-size: 0.5rem;
}

.text-right {
	text-align: right;
}

</style>