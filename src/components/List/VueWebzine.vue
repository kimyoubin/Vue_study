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
      <div
        :style="{ backgroundImage : 'url(' + item.src + ')' }" 
        class="img-area"
      ></div>
      <dl>
        <dt>{{ item.title }}</dt>
        <dd>{{ item.date }}</dd>
      </dl>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'VueWebzine',
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
    // console.log('Webzine component');
  },
  methods: {
  }
}
</script>

<style scoped lang="scss">
ul {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  font-size: 13px;
  li {
    position: relative;
    width: 48%;
    margin-bottom: 30px;
    overflow: hidden;
    cursor: pointer;
    transition: all .4s;
    &::before {
      content: '';
      display: block;
      position: absolute;
      width: 100%;
      height: 35%;
      background: linear-gradient(0, rgba(255, 255, 255, 0), rgba(255, 255, 255, 0.5));
    }
    &:hover {
      &::after {
        content: '';
        display: block;
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border: 4px solid #ffbb5e;
        
      }
    }
    .img-area {
      width: 100%;
      height: 300px;
      background-size: cover;
      background-position: center;
    }
  }
}
dl {
  position: absolute;
  top: 20px;
  left: 20px;
  dt { 
    margin-bottom: 10px;
    font-size: 14px; 
    font-weight: bold;
  }
  dd {
    font-size: 13px;
    &.date {
      margin-bottom: 5px;
    }
  }
}
</style>
