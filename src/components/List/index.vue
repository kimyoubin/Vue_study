<template>
  <div>   
    <!--       
      * v-bind:is="컴포넌트명" : vue에서 동적으로 컴포넌트를 생성하며 전환효과를 주기 위해 사용할 수 있다.
      * keep-alive : 비활성 컴포넌트 인스턴스를 파괴하지 않고 캐시한다. 
      * keep-alive 적용 전 : 전환이 일어날때마다 생성과 소멸을 반복하며 data가 유지되지 않음! 
        그래서 전환이 일어날때마다 번쩍거리는 느낌이 있음.
      * keep-alive 적용 후 : created에 캐시되어 다른 컴포넌트에 갔다와도 페이지의 새로고침이 발생하기 전까지 data가 유지 된다.
        그래서 전환이 일어날때마다 번쩍거리지 않는다!
    -->
    <keep-alive>
      <!-- 
        2. 각각의 컴포넌트를 부른 뒤 컴포넌트 type이 일치할때마다 보일 수 있게 v-if문을 걸어준다. 
      -->
      <!-- 
        4. 각각의 컴포넌트에 app.vue에서 바인딩한 type을 props해준다.
      -->
      <!-- 
        6. 자식 컴포넌트에서 받은 input이벤트를 @input으로 받아 modalData와 함께 $emit으로 부모에게 한번 더 전달해준다.
      -->
      <youbin-gallery 
        v-if="type === 'gallery'"
        :items="items"
        v-model="modalData"
        @input="$emit('input', modalData)"
        @click="$emit('click')" />

      <youbin-table
        v-else-if="type === 'table'"
        :items="items"
        v-model="modalData"
        @input="$emit('input', modalData)"
        @click="$emit('click')" />

      <youbin-webzine
        v-else-if="type === 'webzine'"
        :items="items"
        v-model="modalData"
        @input="$emit('input', modalData)"
        @click="$emit('click')" />
    </keep-alive> 
  </div>
</template>

<script>
import YoubinGallery from '@/components/YoubinList/YoubinGallery.vue'
import YoubinTable from '@/components/YoubinList/YoubinTable.vue'
import YoubinWebzine from '@/components/YoubinList/YoubinWebzine.vue'

export default {
  components: { YoubinGallery, YoubinTable, YoubinWebzine },
  name: 'YoubinList',
  props: {   
    type: {
      type: String,
    },
    items: {
      type: Array,
    }
  },
  data() {
    return {
      modalData: {}
    }
  },
  methods: {
    
  },
  mounted() {
    console.log('modalData :: ',this.modalData);
  }
}
</script>

<style scoped lang="scss">

</style>
