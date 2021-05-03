<template>
  <vue-layout>
    <div class="wrap">
        <!-- 
          3. button을 클릭할때마다 changeList()가 string값을 인자값으로 넘겨준다.
          여기서 listType을 자식컴포넌트인 YoubinList/index.vue에게 :type이라는 이름으로 바인딩해준다.
          그래서 클릭할때마다 string값에 따라 YoubinList/index.vue에서 걸어준 v-if에 맞춰 보여지는것임 
        -->
        <ul class="btn-area">
          <li><button @click="changeList('gallery')">gallery</button></li>
          <li><button @click="changeList('table')">table</button></li>
          <li><button @click="changeList('webzine')">webzine</button></li>
        </ul>   

        <!--
          7. 자식에게 받은 modalData를 v-model="modalData"로 연결시켜 준다.
        -->
        <vue-list
          :type="listType" 
          :items="listData" 
          v-model="modalData" 
          @click="modalActive = true"
        ></vue-list>

        <!-- 
          8. <vue-list />에서 연결한 v-model="modalData"로 리스트를 클릭할때마다 팝업에 각각의 item의 data가 들어가게 된다.
        -->
        <vue-modal
          v-if="modalActive"
          @close="modalClose">
          <dl>
            <dt>{{ modalData.title }}</dt>
            <dd class="date">{{ modalData.writer }}</dd>
            <dd class="img"><img :src="modalData.src"></dd>
          </dl>
        </vue-modal>
    </div>
  </vue-layout>
</template>

<script>
import VueLayout from '@/layouts/index.vue'
import VueList from '@/components/List/index.vue'
import VueModal from '@/components/Modal/index.vue'

export default {
  name: 'List',
  components: { VueLayout, VueList, VueModal },
  data() {
    return {
      listType: 'gallery',
      modalActive: false,
      modalData: {},
      listData: [
        {
          number: '1',
          title: 'Youbin list',
          writer: 'youbin',
          date: '2021-04-01',
          views: 0,
          src: require('@/assets/images/1.jpg'),
          alt: 'kakao friends',
          mark: '1'
        },
        {
          number: '2',
          title: 'Youbin list2',
          writer: 'youbin',
          date: '2021-07-05',
          views: 0,
          src: require('@/assets/images/2.jpg'),
          alt: 'kakao friends',
          mark: '2'
        },
        {
          number: '3',
          title: 'Youbin list3',
          writer: 'shinho',
          date: '2021-10-06',
          views: 0,
          src: require('@/assets/images/3.jpg'),
          alt: 'kakao friends',
          mark: '3'
        },
        {
          number: '4',
          title: 'Youbin list4',
          writer: 'youbin',
          date: '2021-10-30',
          views: 0,
          src: require('@/assets/images/4.jpg'),
          alt: 'kakao friends',
          mark: '4'
        },
        {
          number: '5',
          title: 'Youbin list5',
          writer: 'youbin',
          date: '2021-05-05',
          views: 0,
          src: require('@/assets/images/5.jpg'),
          alt: 'kakao friends',
          mark: '5'
        },
        {
          number: '6',
          title: 'Youbin list5',
          writer: 'youbin',
          date: '2021-05-05',
          views: 0,
          src: require('@/assets/images/6.jpg'),
          alt: 'kakao friends',
          mark: '6'
        }
      ]
    }
  },
  methods: {
    changeList: function (type) {
      // 버튼을 클릭할때마다 string값을 넘겨준다.
      // console.log('type ::', type);
      this.listType = type
    },
    modalClose: function () {
      this.modalActive = false
    },
  },
  // 감시할 데이터를 지정하고 그 데이터가 바뀌면 함수를 실행함 
  // vue 인스턴스의 데이터 변경을 관찰하고 이에 반응함
  watch: {
    // 조회수 올리기
    // v-model="modalData"로 연결 된 modalData함수가 팝업을 클릭릭할때마다 views가 ++된다.
    modalData: function () {
      ++this.modalData.views;
    }
  }
}
</script>

<style scoped lang="scss">
.wrap {
  max-width: 720px;
  margin: 0 auto;
  padding: 70px 0;
}
.index {
  padding: 30px;
}
.btn-area {
  display: flex;
  margin-bottom: 30px;
  li {
    button {
      width: 100px;
      height: 35px;
      color: #fff;
      font-weight: bold;
    }
    &:nth-child(1) {
      button {
        background-color: #fe4247;
      }
    }
    &:nth-child(2) {
      button {
        background-color: #66b5ff;
      }
    }
    &:nth-child(3) {
      button {
        background-color: #ffbb5e;
      }
    }
    &:nth-child(4) {
      position: fixed;
      right: 0;
      top: 0;
      z-index: 9999;
      button {
        background-color: #00c947;
      }
    }
  }
}

.modal {
  dl {
    dt {
      margin-bottom: 5px;
      font-size: 15px;
      font-weight: bold;
    }
    dd {
      font-size: 13px;
      &.date {
        margin-bottom: 20px;
      }
      &.img {
        width: 400px;
        height: 400px;
        img {
          width: 100%;
        }
      }
    }
  }
}
</style>

