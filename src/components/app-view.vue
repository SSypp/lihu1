<template>

  <el-container class="app-container" :class="{
    'mini-side': isCollapse,
    'hide-side': hideSide
  }">
    <el-aside class="app-side" :width="hideSide ? '0' : sideWidth + 'px'" style="background: #338ace;">
      <div class="app-header-logo-box" :style="{height: headerHeight + 'px', color: theme.theme.activeTextColor}">
        <span class="header-logo-text">后台管理系统</span>
      </div>
      <div class="app-header-logo-box1" :style="{height: headerHeight + 'px', color: theme.theme.activeTextColor}">
        <img src="../assets/logo.png" class="logo-box" alt="logi">
        <span class="header-logo-text1">后台管理系统</span>
      </div>
      <app-side :collapse="isCollapse" :theme="theme.theme" class="aside-bg"></app-side>
    </el-aside>
    <el-container style="overflow-x: auto">
      <el-header class="app-header" :height="headerHeight + 'px'">
        <app-header @switch="handleSideSwitch" @set-theme="handleSetTheme" @hide-side="handleSwitchHideSide"></app-header>
      </el-header>
      <el-main class="app-body">
        <el-container style="height: 100%;min-height: 100%;overflow: auto" id="appBody">
          <el-main class="app-page-body">
            <router-view></router-view>
          </el-main>
        </el-container>
      </el-main>
    </el-container>
    <m-back-top body-id="appBody"></m-back-top>
  </el-container>

</template>
<script type="text/javascript">
import AppHeader from '@/components/app-header'
import AppSide from '@/components/app-side'
export default {
  name: 'app-view',
  data () {
    return {
      isCollapse: false,
      hideSide: false,
      sideWidth: 200,
      headerHeight: 50,
      theme: { theme: {} }
    }
  },
  components: {
    AppHeader,
    AppSide
  },
  methods: {
    handleSideSwitch (val) {
      this.isCollapse = val
      this.sideWidth = val ? 60 : 200
    },
    handleSwitchHideSide () {
      this.hideSide = !this.hideSide
    },
    handleSetTheme (theme) {
      this.theme = theme
    }
  }
}
</script>
<style type="text/css">
.app-container {
  margin: 0 auto;
  position: absolute;
  width: 100%;
  height: 100%;
}
.app-container .app-header {
  padding: 0;
  background: #15afd9;
  overflow: visible;
  z-index: 100;
}
.app-container .app-side {
  width: 200px;
  transition: all 0.5s ease;
}
.app-container .app-body {
  background: #ecf0f5;
  padding: 0;
}
.app-container .app-footer {
  background: #fff;
  border-top: solid 1px rgba(48, 54, 62, 0.14);
}
.app-container .app-page-body {
  overflow: visible;
  padding: 0px;
}
.app-header-logo-box {
  padding: 15px;
  box-sizing: border-box;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  background-color: #15afd9;
  color: #fff;
  text-align: center;
  font-size: 18px;
  font-weight: bold;
}
/*logo*/
.app-header-logo-box1 {
  height: 80px !important;
  background-color: #338ace;
  color: #fff;
  padding: 15px;
  box-sizing: border-box;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  color: #fff;
  text-align: center;
  font-size: 12px;
  border-bottom: 1px solid #fff;
}
.logo-box{
  display: inline-block;
  width: 40px;
  vertical-align: middle;
}
.header-logo-text1{
  margin-bottom: 10px!important;
}
.aside-bg{
  background-color: #338ace;
  color: #fff !important;
}
element.style {
  color: #fff!important;
}
/* mini-side
.app-container.mini-side .app-side {
  overflow: visible;
}
.app-container.mini-side .app-side .el-menu--collapse {
  width: 60px;
}
.app-container.mini-side .header-logo {
  margin-left: -10px;
}
.app-container.mini-side .header-logo-text {
  opacity: 0;
}
hide-side
.app-container.hide-side .app-side {
  display: none;
} */
</style>
