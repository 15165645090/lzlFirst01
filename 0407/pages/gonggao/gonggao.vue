<template>
  <list>
    <!-- 注意事项: 不能使用 index 作为 key 的唯一标识 -->
    <cell v-for="(item, index) in dataList" :key="item.id">
      <text>{{item.name}}</text><br>
    </cell>
  </list>
</template>

<script>
  export default {
    data () {
      return {
        dataList: [{id: "1", name: '公告列表1'}, {id: "2", name: '公告列表2'}, {id: "3", name: '公告列表3'}, {id: "4", name: '公告列表4'}, {id: "5", name: '公告列表5'}, {id: "6", name: '公告列表6'}]
      }
    }
  }
</script>