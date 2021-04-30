<template>
  <table>
    <thead>
      <tr>
        <th>번호</th>
        <th>제목</th>
        <th>글쓴이</th>
        <th>날짜</th>
        <th>조회수</th>
      </tr>
    </thead>
    <tbody>
      <!-- 
        1. 각 컴포넌트에 v-for를 사용하여 app.vue에 있는 data를 불러온다. 
      -->

      <!-- 
        5. 클릭할때마다 modal을 띄우기 위한 @click이벤트를 $emit으로 걸어준다.        
          - 'input' : input이벤트를 부모에게 item과 함께 전달해준다. 
          - 'click' : modal을 띄위기 위한 이벤트를 부모에게 전달시킨다.
      -->
      <tr 
        v-for="(item, key) in items"
        :key="key"
        @click="$emit('input', item); $emit('click')">
        <td>{{ item.number }}</td>
        <td>{{ item.title }}</td>
        <td>{{ item.writer }}</td>
        <td>{{ item.date }}</td>
        <td>{{ item.views }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'YoubinTable',
  props: {
    items: {
      type: Array
    }
  },
  created() {
    console.log('Table component');
  },
}
</script>

<style scoped lang="scss">

table {
  width: 100%;
  font-size: 14px;
  text-align: center;
  border-collapse: collapse;
  border-top: 1px solid #b4b4b4;
  border-left: 1px solid #b4b4b4;
  th, td {
    height: 70px;
    border-right: 1px solid #b4b4b4; 
    border-bottom: 1px solid #b4b4b4; 
  }
  th {
    background-color: #f3f3f3;
  }
  tr {
    background-color: #fff;
    transition: all .4s;
    cursor: pointer;
    &:hover {
      background-color: #f3f3f3;
    }
  }
}
</style>
