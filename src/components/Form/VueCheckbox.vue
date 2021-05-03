<template>
	<div class="checkbox">
        <input 
            type="checkbox"
            :name="name"
            :id="id"
            :checked="value"
            @input="change">
        <label :for="id"><slot></slot></label>
    </div>
</template>

<script>
export default {
	name: 'VueCheckbox',
	props: {
        name: {
            type: String,
            default: ''
        },
        id: {
            type: String,
            default: ''
        },
        value: {
            type: String,
            default: ''
        },
        for: {
            type: String,
            derault: ''
        }
	},
	data() {
		return {
		}
	},
	methods: {
		change: function($event) {
			this.$emit('input', $event.target.value)
		}
	}
}
</script>

<style lang="scss" scoped>
.checkbox {
    input {
        display: none;
        &:checked {
            +label {
                    &:before {
                    left: 4px;
                    top: 1px;
                    width: 14px;
                    height: 9px;
                    border: 3px solid #fe4247;
                    border-top: 0;
                    border-right: 0;
                    transform: rotate(-45deg);
                    z-index: 1;
                }
            }
        }
        +label {
            position: relative;
            display: block;
            padding-left: 30px;
            color: #333;
            text-align: left;
            font-size: 14px;
            &:before,
            &:after {
                content: '';
                display: inline-block;
                position: absolute;
                margin: auto;
            }                                  
            &:after {
                top: 0;
                bottom: 0;
                left: 0;
                width: 22px;
                height: 22px;
                background-color: #fff;
                border: 1px solid #d1d1d1;
            }
        }
    }
}
</style>
