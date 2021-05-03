<template>
  <div class="list">
      <!-- 
        3. button을 클릭할때마다 changeList()가 string값을 인자값으로 넘겨준다.
        여기서 listType을 자식컴포넌트인 YoubinList/index.vue에게 :type이라는 이름으로 바인딩해준다.
        그래서 클릭할때마다 string값에 따라 YoubinList/index.vue에서 걸어준 v-if에 맞춰 보여지는것임 
      -->
      <ul class="btn-area">
        <li><button @click="changeList('gallery')">갤러리형</button></li>
        <li><button @click="changeList('table')">테이블형</button></li>
        <li><button @click="changeList('webzine')">웹진형</button></li>
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
          <dt>제목 : {{ modalData.title }}</dt>
          <dd>작성자 : {{ modalData.writer }}</dd>
          <dd>조회수 : {{ modalData.views }}</dd>
          <dd><img :src="modalData.src"></dd>
        </dl>
      </vue-modal>
  </div>
</template>

<script>
import VueList from '@/components/List/index.vue'
import VueModal from '@/components/Modal/index.vue'

export default {
  name: 'List',
  components: { VueList, VueModal },
  data() {
    return {
      listType: 'gallery',
      modalActive: false,
      modalData: {},
      listData: [
        {
          number: '1',
          title: '유빈 리스트입니다',
          writer: '유빈',
          date: '2021-04-01',
          views: 0,
          src: require('@/assets/images/1.jpg'),
          alt: '하연이1',
          mark: '1'
        },
        {
          number: '2',
          title: '뷰를 공부하고있습니당',
          writer: '유빈',
          date: '2021-07-05',
          views: 0,
          src: require('@/assets/images/2.jpg'),
          alt: '하연이2',
          mark: '2'
        },
        {
          number: '3',
          title: '이번 과제는 너무 어렵네요ㅠㅠ',
          writer: '유빈',
          date: '2021-10-06',
          views: 0,
          src: require('@/assets/images/3.jpg'),
          alt: '하연이3',
          mark: '3'
        },
        {
          number: '4',
          title: '배움은 끝이 없어요...',
          writer: '유빈',
          date: '2021-10-30',
          views: 0,
          src: require('@/assets/images/4.jpg'),
          alt: '하연이4',
          mark: '4'
        },
        {
          number: '5',
          title: '졸립다ㅠㅠ',
          writer: '유빈',
          date: '2021-05-05',
          views: 0,
          src: require('@/assets/images/5.jpg'),
          alt: '하연이5',
          mark: '5'
        }
      ]
    }
  },
  methods: {
    changeList: function (type) {
      // 버튼을 클릭할때마다 string값을 넘겨준다.
      console.log('type ::', type);
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
.list {
  max-width: 720px;
  margin: 0 auto;
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
        background-color: #ffb819;
      }
    }
    &:nth-child(2) {
      button {
        background-color: #ec2e51;
      }
    }
    &:nth-child(3) {
      button {
        background-color: #199fff;
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
</style>

