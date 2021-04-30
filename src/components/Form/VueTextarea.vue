<template>
	<textarea 
        :name="name" 
        :id="id"
        :value="value"
        @input="change">
    </textarea>
</template>

<script>
export default {
	name: 'VueTextarea',
	props: [
        'name', 'id', 'value'
	],
	data() {
		return {
		}
	},
	methods: {
        change: function($event) {
            this.$emit('input', $event.target.value);
        }
	}
}
</script>

<style scoped>
textarea {
	width: 100%;
	height: 150px;
	padding: 10px;
	margin-bottom: 15px;
	font-size: 18px;
	color: #333;
	border: 1px solid #8e8e8e;
    resize: none;
}

textarea::placeholder {
	font-size: 16px;
	color: #8e8e8e;
}


</style>
