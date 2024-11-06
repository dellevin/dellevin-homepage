<template>
    <div class="container">
      <el-tabs v-model="activeName" type="card">
        <el-tab-pane label="自述 · 平凡" name="1">
          用户管理


        </el-tab-pane>
        <el-tab-pane label="我的网站" name="2">
          配置管理

        </el-tab-pane>
        <el-tab-pane label="技能" name="3">
          配置管理

        </el-tab-pane>
        <el-tab-pane label="书签" name="4">
          <MyBookmarks> </MyBookmarks>

        </el-tab-pane>

      </el-tabs>
     
    </div>
  </template>
  
  <script>
  import MyBookmarks from '../view/my-bookmarks.vue';
  export default {
    name: 'MyContent',
    components: {
      MyBookmarks
    },
    data() {
      return {
        activeName: '1'
      };
    },
    methods: {

    }
  };
  </script>
  
  <style scoped>
  .container{
      padding-left: 20px;
      padding-right: 20px;
      padding-top: 20px;
      padding-bottom: 20px;

      min-height: 920px;
      margin-top: 30px;
      width: 75%;
      border-radius: 10px;
      background: #fff;
      box-shadow: 0 4px 8px 6px rgba(7, 17, 27, .06);
      transition: all .3s;
  }
  </style>
  