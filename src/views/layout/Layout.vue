<template>
  <div class="app-wrapper" :class="{hideSidebar:!sidebar.opened}">
    <!--导航栏-->
    <navbar></navbar>
    <!--侧边栏-->
    <div class="sidebar-wrapper">
      <sidebar class="sidebar-container"></sidebar>
    </div>
    <!--中间内容-->
    <div class="main-container">
      <!--内容区的导航-->
      <levelbar></levelbar>
      <!--主题内容-->
      <app-main></app-main>
    </div>
  </div>
</template>

<script>
export default {
  name: 'layout'
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
  .app-wrapper {
    @include clearfix;
    position: relative;
    height: 100%;
    width: 100%;
    &.hideSidebar {
      .sidebar-wrapper {
        transform: translate(-140px, 0);
        .sidebar-container {
          transform: translate(132px, 0);
        }
        &:hover {
          transform: translate(0, 0);
          .sidebar-container {
            transform: translate(0, 0);
          }
        }
      }
      .main-container {
        margin-left: 40px;
      }
    }
    .sidebar-wrapper {
      width: 180px;
      position: fixed;
      top: 50px;
      bottom: 0;
      left: 0;
      z-index: 1001;
      overflow: hidden;
      transition: all .28s ease-out;
    }
    .sidebar-container {
      transition: all .28s ease-out;
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      right: -17px;
      overflow-y: scroll;
    }
    .main-container {
      min-height: 100%;
      transition: all .28s ease-out;
      margin-left: 180px;
      padding-top: 50px;
    }
  }
</style>
