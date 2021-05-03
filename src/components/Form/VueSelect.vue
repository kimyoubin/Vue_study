<template>
    <div 
        :tabindex="tabIndex"
        @blur="isActive = false"
        @focus="isActive"        
        class="selectbox">
        <button 
            @click="toggleEvent"
            :class="{'on' : isActive}">{{ selected }}</button>
        <div 
            v-if="isActive"
            :class="{'on' : isActive}"
            class="selectbox-option">
            <ul>              
                <!-- li 클릭시 selected를 item.option data로 바꿔줌 -->
                <li 
                    v-for="(item, key) in items"
                    :key="key"
                    @click="selectOption(item)">{{ item.option }}</li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
	name: 'VueSelect',
	props: {
        items: {
            type: Array,
            require: true
        },
        tabIndex: {
            type: Number,
            require: false,
            default: 0
        }
    },
	data() {
		return {
			isActive: false,
            selected: 'all',
		}
	},
    methods: {
        toggleEvent: function () {            
            this.isActive = !this.isActive
        },
        selectOption: function(item) {
            console.log(item);
            this.selected = item.option;
            this.isActive = false;
        },
        // blurEvent: function () {
        //     this.
        //     console.log('닫혀라');
            
        // }
    }
}
</script>

<style lang="scss" scoped>
.selectbox {
    width: 100%;   
    position: relative;
    button, li {
        width: 100%;
        height: 50px;
        padding: 10px;
        font-size: 14px;
        text-align: left;
        color: #333;	
        background: #fff;
    }
    button {
        position: relative;
        background: #fff;
        &.on {
            border: 1px solid rgb(228, 228, 228);
            border-bottom: 0;
            &::after {
                transform: rotate(180deg);
            }
        }
        &::after {
            content: '';
            display: block;
            position: absolute;
            top: 20px;
            right: 10px;
            width: 0;
            height: 0;
            border-top: 7px solid #ddd;
            border-left: 7px solid transparent;
            border-right: 7px solid transparent;
        }
    }
    .selectbox-option {
        position: absolute;
        top: 50px;
        left: 0;
        right: 0;
        max-height: 200px;
        background-color: #fff;
        // overflow-y: auto;
        // &::-webkit-scrollbar {
        //     width: 7px;
        //     background-color: transparent;
        // }
        // &::-webkit-scrollbar-thumb {
        //     width: 7px;
        //     border-radius: 5px;
        //     background-color: #000;
        // }
        &.on {
            ul {
                border: 1px solid rgb(228, 228, 228);
                border-top: 0;
            }                
        }
        ul {
            box-shadow: 0 10px 10px rgba(0,0,0,.05);
            li {
                display: flex;
                align-items: center;
                width: 100%;
                height: 50px;
                cursor: pointer;
                &:hover {
                    background-color: #f3f3f3;
                }
            }
        }
    }
}
</style>
