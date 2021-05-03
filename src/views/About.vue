<template>
	<vue-layout>
		<div class="wrap">
			<ul class="form-area">
				<li>
					<vue-input
						v-model="inputData"
						type="text"
						placeholder="Please enter your name"
					></vue-input>
				</li>
				<li>
					<vue-input
						v-model="inputData"
						type="email"
						placeholder="Please enter your email"
					></vue-input>
				</li>
				<li>
					<vue-select
						:items="listData"
					></vue-select>
				</li>
				<li>
					<vue-textarea
						v-model="textareaData"
						placeholder="Please enter your inquiry"
					></vue-textarea>
				</li>
				<li>
					<vue-checkbox
						v-model="checkData"
						name="check"
						id="check"
					>Do you agree?</vue-checkbox>
				</li>
			</ul>
		</div>
	</vue-layout>
</template>

<script>
import VueLayout from '@/layouts/index.vue'
import VueInput from '../components/Form/VueInput.vue'
import VueSelect from '../components/Form/VueSelect.vue'
import VueTextarea from '../components/Form/VueTextarea.vue'
import VueCheckbox from '../components/Form/VueCheckbox.vue'

export default {
	name: 'About',
	components: { VueLayout, VueInput, VueSelect, VueTextarea, VueCheckbox },
	data() {
		return {
			inputData: '',
			textareaData: '',
			checkData: '',
			listData: [
				{
					option: 'list1'
				},
				{
					option: 'list2'
				},
				{
					option: 'list3'
				},
				{
					option: 'list4'
				},
			]
		}
	}
}
</script>

<style lang="scss" scoped>
.wrap {
	max-width: 720px;
	margin: 0 auto;
	padding: 70px 0;
}
.form-area {
	li {
		margin-bottom: 15px;
	}
}

</style>
