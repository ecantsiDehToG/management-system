<template>

  <el-container>
    <el-header>
      <el-row>
        <el-col :span="4">
          <div class="grid-content bg-purple">itheima logo</div>
        </el-col>
        <el-col :span="16">
          <div class="grid-content bg-purple-dark">电商后台管理系统</div>
        </el-col>
        <el-col :span="4">
          <div class="grid-content .bg-purple-light"><a href="#">退出系统</a></div>
        </el-col>
      </el-row>
    </el-header>
    <el-container>
      <el-aside width="200px">
        <el-col :span="12">
          <el-menu default-active="2"
                   class="el-menu-vertical-demo"
                   @open="handleOpen"
                   @close="handleClose">
            <el-submenu index="1">
              <template slot="title">
                <i class="el-icon-location"></i>
                <span>用户管理</span>
              </template>
              <el-menu-item-group>
                <el-menu-item index="1-1">选项1</el-menu-item>
                <el-menu-item index="1-2">选项2</el-menu-item>
              </el-menu-item-group>

            </el-submenu>

          </el-menu>
        </el-col>
      </el-aside>
      <el-main>Main</el-main>
    </el-container>
  </el-container>

</template>

<script type="text/javascript">
export default {

}
</script>

<style scoped>
.el-header,
.el-footer {
  padding: 0;
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  height: 100%;
  line-height: 200px;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
  height: 100%;
  line-height: 160px;
}

.el-container {
  height: 100%;
}

.el-row {
  margin-bottom: 20px;
}
.el-col {
  border-radius: 4px;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple-light {
  background: #e5e9f2;
}
.el-aside > .el-col {
  width: 100%;
  height: 100%;
}
</style>
