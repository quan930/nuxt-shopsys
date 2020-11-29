<template>
  <div style="height: 100vh">
    <el-container id="con">
      <el-aside style="width: 150px">
        <el-menu
          style="height: 100vh;width: 150px"
          :default-active="view"
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
     * 切换路由
     * @param index
     * @param indexPath
     */
    showPage(index, indexPath) {
      switch (index) {
        case '1':
          this.$router.push('/')
          break
        case '2':
          this.$router.push('/books')
          break
        case '3':
          this.$router.push('/bookinfo')
          break
        case '4':
          this.$router.push('/bookadd')
      }
    }
  },
  watch: {
    //监控路由更改
    $route: {
      handler: function(val, oldVal){
        switch (val.name) {
          case 'books':
            this.view='2'
            break
          case 'bookadd':
            this.view='4'
            break
          case 'bookinfo':
          case 'bookinfo-id':
            this.view='3'
            break
          default:
            this.view='1'
            break
        }
        console.log(val);
        // Object.assign(this.routeParams, val.params)
      },
      // 深度观察监听
      deep: true
    }
  },
  mounted() {
    switch (this.$route.name) {
      case 'books':
        this.view='2'
        break
      case 'bookadd':
        this.view='4'
        break
      case 'bookinfo':
      case 'bookinfo-id':
        this.view='3'
        break
      default:
        this.view='1'
        break
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
