<template>
	<input 				
		:type="type"
		:placeholder="placeholder"
		:value="value"
		@click="isActive = true"
		@blur="isActive = false"
		@input="change" 
		:class="{ 'on' : isActive }">
</template>

<script>
export default {
	name: 'VueInput',
	props: {
		type: {
			type: String,
			default: ''
		},	
		placeholder: {
			type: String,
			default: ''
		},	
		value: {
			type: String,
			default: ''
		},	
	},
	data() {
		return {
			isActive: false,
		}
	},
	methods: {
		// 부모에게 input이벤트를 던저준다.
		// 반드시 input이벤트여야 함, v-model은 input이라는 이벤트로 받기 때문
		change: function($event) {
			this.$emit('input', $event.target.value)
		}
	}
}
</script>

<style lang="scss" scoped>
input {
	width: 100%;
	height: 50px;
	padding: 10px;
	font-size: 14px;
	color: #333;
	background-color: #fff;
	&.on {
		border: 1px solid rgb(228, 228, 228);
		box-shadow: 0 10px 10px rgba(0,0,0,.05);
	}
}

input {
	&::placeholder{
		font-size: 14px;
		color: #ddd;
	}
}

</style>
