<template>
    <div 
        :tabindex="tabIndex"
        @blur="isActive = false;"        
        class="selectbox">
        <button 
            @click="toggleEvent"
            :class="{'on' : isActive}">{{ selected }}</button>
        <div 
            v-if="isActive"
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
            selected: '선택해주세요',
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

<style scoped>
.selectbox {
    width: 100%;   
    position: relative;
}

.selectbox button, .selectbox li {
    width: 100%;
    height: 50px;
    padding: 10px;
    font-size: 18px;
    text-align: left;
	color: #333;	
}

.selectbox button {
    position: relative;
    border: 1px solid #8e8e8e;
}

.selectbox button.on::after{
    transform: rotate(180deg);
}

.selectbox button::after {
    content: '';
    display: block;
    position: absolute;
    top: 20px;
    right: 10px;
    width: 0;
	height: 0;
	border-top: 7px solid #000;
	border-left: 7px solid transparent;
	border-right: 7px solid transparent;
}

.selectbox .selectbox-option {
    position: absolute;
    top: 50px;
    left: 0;
    right: 0;
    max-height: 200px;
    border-left: 1px solid #8e8e8e;
    border-right: 1px solid #8e8e8e;
    border-bottom: 1px solid #8e8e8e;
    background-color: #fff;
    overflow-y: auto;
}

.selectbox .selectbox-option::-webkit-scrollbar {
	width: 7px;
    background-color: transparent;
}

.selectbox .selectbox-option::-webkit-scrollbar-thumb {
	width: 7px;
    border-radius: 5px;
    background-color: #000;
}

.selectbox ul li {    
    display: flex;
    align-items: center;
    width: 100%;
    height: 50px;
    cursor: pointer;
}

.selectbox ul li:hover {
    background-color: #f3f3f3;
}

</style>
