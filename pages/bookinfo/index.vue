<template>
  <div>
    <el-row>
      <el-col :span="4" :offset="2">
        <h1>商品详情</h1>
      </el-col>
    </el-row>
    <el-row style="margin-top: 20vh">
      <el-col :span="6" :offset="8">
        <el-input
          placeholder="查询商品-输入商品id"
          v-model="searchid"
          clearable>
        </el-input>
      </el-col>
      <el-col :span="2">
        <el-button type="primary" @click="search">查询</el-button>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  data:function() {
    return{
      searchid:''
    }
  },
  methods:{
    search:function () {
      this.$router.push('/bookinfo/'+this.searchid)
    }
  },
  head: {
    title: '商品详情',
    meta: [
      {hid: 'description', name: 'description', content: 'bookinfo page description'}
    ]
  }
}
</script>

<style scoped>

</style>
