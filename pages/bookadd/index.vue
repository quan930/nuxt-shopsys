<template>
  <div>
    <el-row>
      <el-col :span="4" :offset="2">
        <h1>添加商品</h1>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="12" :offset="6">
        <el-form ref="form" :model="form" label-width="80px">
          <el-form-item label="商品id">
            <el-input v-model="form.id"></el-input>
          </el-form-item>
          <el-form-item label="商品名称">
            <el-input v-model="form.name"></el-input>
          </el-form-item>
          <el-form-item label="商品价格">
            <el-input v-model="form.price"></el-input>
          </el-form-item>
          <el-form-item label="商品库存">
            <el-input v-model="form.count"></el-input>
          </el-form-item>
          <el-form-item label="作者">
            <el-input v-model="form.author"></el-input>
          </el-form-item>
          <el-form-item label="出版社">
            <el-input v-model="form.Press"></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="onSubmit">立即创建</el-button>
            <el-button @click="cancel">取消</el-button>
          </el-form-item>
        </el-form>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data:function (){
    return{
      form:{
        id: null,
        name: null,
        price: null,
        count: null,
        author: null,
        Press: null
      }
    }
  },
  methods:{
    onSubmit:async function () {
      try {
        const {data} = await axios.post('http://localhost:4000/book/', {
          id: this.form.id,
          name: this.form.name,
          price: this.form.price,
          count: this.form.count,
          author: this.form.author,
          Press: this.form.Press
        })
        console.log(data)
        this.cancel();
        await this.$router.push('/books')
      } catch (e) {
        error({statusCode: 500, message: '服务出错了稍等一下'})
      }
    },
    cancel:function (){
      this.form={
        id: null,
        name: null,
        price: null,
        count: null,
        author: null,
        Press: null
      }
    }
  }
}
</script>

<style scoped>

</style>
