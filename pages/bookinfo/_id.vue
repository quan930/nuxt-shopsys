<template>
  <div>
    <el-row>
      <el-col :span="4" :offset="2">
        <h1>商品详情</h1>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="12" :offset="6">
        <el-form ref="form" :model="book" label-width="80px">
          <el-form-item label="商品id">
            <el-input v-model="book.id" :disabled="true"></el-input>
          </el-form-item>
          <el-form-item label="商品名称">
            <el-input v-model="book.name" :disabled="true"></el-input>
          </el-form-item>
          <el-form-item label="商品价格">
            <el-input v-model="book.price" :disabled="true"></el-input>
          </el-form-item>
          <el-form-item label="商品库存">
            <el-input v-model="book.count" :disabled="true"></el-input>
          </el-form-item>
          <el-form-item label="作者">
            <el-input v-model="book.author" :disabled="true"></el-input>
          </el-form-item>
          <el-form-item label="出版社">
            <el-input v-model="book.Press" :disabled="true"></el-input>
          </el-form-item>
        </el-form>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  async asyncData ({ params, error }) {
    try {
      const { data } = await axios.get(`http://localhost:4000/book/${params.id}`)
      // eslint-disable-next-line no-console
      console.log(data)
      return { book: data }
    } catch (e) {
      error({ statusCode: 404, message: `商品 ${params.id} 不存在` })
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
