<template>
	<textarea 
        :value="value"
		:placeholder="placeholder"
		@click="isActive = true"
		@blur="isActive = false"
        @input="change"
		:class="{ 'on' : isActive }">
    </textarea>
</template>

<script>
export default {
	name: 'VueTextarea',
	props: {	
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
        change: function($event) {
            this.$emit('input', $event.target.value);
        }
	}
}
</script>

<style lang="scss" scoped>
textarea {
	width: 100%;
	height: 150px;
	padding: 10px;
	margin-bottom: 15px;
	font-size: 14px;
	color: #333;
	background: #fff;
    resize: none;
	&.on {
		border: 1px solid rgb(228, 228, 228);
		box-shadow: 0 10px 10px rgba(0,0,0,.05);
	}
	&::placeholder{
		font-size: 14px;
		color: #ddd;
	}	
}

</style>
