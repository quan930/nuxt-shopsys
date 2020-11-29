<template>
  <div style="height: 100vh">
    <el-container id="con">
      <el-aside>
        <el-menu
          style="height: 100vh;width: 150px"
          default-active="3"
          class="el-menu-vertical-demo"
          background-color="#545c64"
          text-color="#fff"
          active-text-color="#ffd04b"
          @select="showPage">
          <el-menu-item index="1">
            <i class="el-icon-menu"></i>
            <span slot="title">首页</span>
          </el-menu-item>
          <el-menu-item index="2">
            <i class="el-icon-menu"></i>
            <span slot="title">商品列表</span>
          </el-menu-item>
          <el-menu-item index="3">
            <i class="el-icon-document"></i>
            <span slot="title">商品详情</span>
          </el-menu-item>
          <el-menu-item index="4">
            <i class="el-icon-setting"></i>
            <span slot="title">提交商品</span>
          </el-menu-item>
        </el-menu>
      </el-aside>
      <el-main>
        <Nuxt />
      </el-main>
    </el-container>
  </div>
</template>

<script>
export default {
  data () {
    return {
      view:'1'
    }
  },
  methods:{
    /**
     * 切换视图
     * @param index
     * @param indexPath
     */
    showPage(index, indexPath) {
      switch (index) {
        case '1':
          console.log("首页面")
          this.$router.push('/')
          break
        case '2':
          console.log("商品列表页面")
          this.$router.push('/books')
          break
        case '3':
          console.log("商品详情页面")
          this.$router.push('/bookinfo')
          break
        case '4':
          console.log("添加商品页面")
          this.$router.push('/bookadd')
      }
      this.view = index
    }
  }
}
</script>

<style>
body{
  margin: 0;
  padding: 0;
}
</style>
