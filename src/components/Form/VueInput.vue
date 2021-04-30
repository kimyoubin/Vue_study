<template>
	<input 				
		:type="type"
		:placeholder="placeholder"
		:name="name"
		:id="id"
		:value="value"
		@click="isActive = true"
		@blur="isActive = false"
		@input="change" 
		:class="{ 'on' : isActive }">
</template>

<script>
export default {
	name: 'VueInput',
	props: [
		// 부모에서 v-model로 던진값을 value로 받음
		'type', 'placeholder', 'name', 'id', 'value', 'checked'
	],
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

<style scoped>

input {
	width: 100%;
	height: 50px;
	padding: 10px;
	margin-bottom: 15px;
	font-size: 18px;
	color: #333;
	border: 1px solid #8e8e8e;
}

input::placeholder {
	font-size: 16px;
	color: #8e8e8e;
}

input.on {
	border: 1px solid #001ad7;
	transition: all .3s;
}

</style>
