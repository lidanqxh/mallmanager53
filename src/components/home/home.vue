<template>
  <el-container class="container">
    <el-header class="header">
      <el-row>
        <el-col :span="4">
          <div class="grid-content bg-purple">
            <img src="../../assets/logo.png"/>
          </div>
        </el-col>
        <el-col :span="18" class="middle">
          <h3>电商后台管理系统</h3>
        </el-col>
        <el-col :span="2">
          <div class="grid-content bg-purple">
            <a class="logout" @click="logout()" href="#">退出</a>
          </div>
        </el-col>
      </el-row>
    </el-header>
    <el-container>
      <el-aside class="aside" width="200px">
        <el-menu :unique-opened ="true">
          <!--  1 -->
          <el-submenu index="1">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>用户管理</span>
            </template>
            <el-menu-item index="1-1">
              <i class="el-icon-check"></i>
              <span>用户列表</span>
            </el-menu-item>
          </el-submenu>
          <!--  2 -->
          <el-submenu index="2">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>权限管理</span>
            </template>
            <el-menu-item index="1-1">
              <i class="el-icon-check"></i>
              <span>角色列表</span>
            </el-menu-item>
            <el-menu-item index="1-2">
              <i class="el-icon-check"></i>
              <span>权限列表</span>
            </el-menu-item>
          </el-submenu>
          <!--  3 -->
          <el-submenu index="3">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>商品管理</span>
            </template>
            <el-menu-item index="1-1">
              <i class="el-icon-check"></i>
              <span>商品列表</span>
            </el-menu-item>
            <el-menu-item index="1-2">
              <i class="el-icon-check"></i>
              <span>分类参数</span>
            </el-menu-item>
            <el-menu-item index="1-3">
              <i class="el-icon-check"></i>
              <span>商品分类</span>
            </el-menu-item>
          </el-submenu>
          <!--  4 -->
          <el-submenu index="4">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>订单管理</span>
            </template>
            <el-menu-item index="1-1">
              <i class="el-icon-check"></i>
              <span>订单列表</span>
            </el-menu-item>
          </el-submenu>
          <!--  5 -->
          <el-submenu index="5">
            <template slot="title">
              <i class="el-icon-location"></i>
              <span>数据统计</span>
            </template>
            <el-menu-item index="1-1">
              <i class="el-icon-check"></i>
              <span>数据报表</span>
            </el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-main class="main">Main</el-main>
    </el-container>
  </el-container>
</template>

<script>
  export default {
    beforeCreate(){
      const token = localStorage.getItem("token");
      if(!token){
        this.$router.push({name:'login'});
      }
    },
    methods: {
      logout(){
        localStorage.removeItem("token");
        this.$router.push({name:'login'});
      }
    }
  }
</script>

<style>
  .container {
    height: 100%;
  }

  .header {
    background-color: #b3c0d1;
  }

  .aside {
    background-color: #d3dce6;
  }

  .main {
    background-color: #e9eef3;
  }

  .middle {
    text-align: center;
    color: white;
  }

  .logout {
    line-height: 60px;
    text-decoration: none;
  }
</style>
