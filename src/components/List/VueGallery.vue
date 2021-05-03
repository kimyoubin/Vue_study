<template>
  <ul>
    <!-- 
      1. 각 컴포넌트에 v-for를 사용하여 app.vue에 있는 data를 불러온다. 
    -->

    <!-- 
      5. 클릭할때마다 modal을 띄우기 위한 @click이벤트를 $emit으로 걸어준다.        
        - 'input' : input이벤트를 부모에게 item과 함께 전달해준다. 
        - 'click' : modal을 띄위기 위한 이벤트를 부모에게 전달시킨다.
    -->
    <li 
      v-for="(item, key) in items"
      :key="key"
      @click="$emit('input', item); $emit('click')">
      <span class="mark">{{ item.mark }}</span>
      <div 
        :style="{'backgroundImage' : 'url('+ item.src +')'}"
        class="img-area">
      </div>
      <dl>
        <dt>{{ item.title }}</dt>
        <dd class="date">{{ item.date }}</dd>
        <dd class="views">view : {{ item.views }}</dd>
      </dl>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'VueGallery',
  props: {
    items: {
      type: Array
    },
    src: {
      type: String
    },
    alt: {
      type: String
    },
  },
  created() {
    console.log('Gallery component');
  },
}
</script>

<style scoped lang="scss">
ul {
  font-size: 14px;
  li {
    position: relative;
    display: flex;
    height: 150px;
    margin-bottom: 30px;
    background-color: #fff;
    border: 1px solid #ddd;
    overflow: hidden;
    cursor: pointer;
    transition: all .5s;
    &:hover {
      box-shadow: 0 20px 20px rgba(0,0,0,.1);
    }
    .mark {
      position: absolute;
      top: 0;
      left: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      width: 30px;
      height: 30px;
      color: #fff;
      font-size: 13px;
      font-weight: bold;
      background-color: #f5c53b;
      z-index: 1;
    }
    .img-area { 
      width: 375px;
      height: 100%;
      background-size: cover;
      background-position: center;
      overflow: hidden;
      img {
        width: 100%;       
        height: 100%; 
        transition: all .4s;
      }
    }
    
  }
}
dl {
  width: calc(100% - 200px);
  padding: 20px;
  dt { 
    margin-bottom: 10px;
    font-size: 16px; 
    font-weight: bold;
  }
  dd {
    font-size: 13px;
    &.date {
      margin-bottom: 20px;
    }
    &.views {
      text-align: right;
    }
  }
}
</style>
