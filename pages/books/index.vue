<template>
  <div>
    <el-row>
      <el-col :span="4">
        <h1>商品列表</h1>
      </el-col>
    </el-row>
    <el-table :data="books"
              height="500"
              border
              style="width: 100%">
      <el-table-column
        prop="name"
        label="书名">
      </el-table-column>
      <el-table-column
        prop="price"
        label="价格">
      </el-table-column>
      <el-table-column
        prop="author"
        label="作者">
      </el-table-column>
      <el-table-column
        label="详情">
        <template slot-scope="scope">
          <nuxt-link :to="'bookinfo/'+books[scope.$index].id" >
            <el-link type="primary">详情</el-link>
          </nuxt-link>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData ({ error }) {
    try {
      const { data } = await axios.get('http://localhost:4000/book/')
      console.log(data)
      return { books: data}
    } catch (e) {
      error({ statusCode: 500, message: '服务出错了稍等一下' })
    }
  },
  data () {
    return {}
  },
  head: {
    title: '商品列表',
    meta: [
      { hid: 'description', name: 'description', content: '商品列表' }
    ]
  }
}
</script>

<style scoped>

</style>
