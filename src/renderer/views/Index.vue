<template>
  <div id="index">
    <el-container>
      <el-header height="40px">
        <!-- <img src="@/renderer/assets/logo.png" draggable="false" /> -->
        <div class="headTitle">Cute Launcher</div>
        <el-popover
          placement="top-start"
          width="100"
          trigger="hover"
          content="open cute for github"
        >
          <!-- <el-button slot="reference">hover 激活</el-button> -->
          <el-button
            slot="reference"
            class="headClick"
            type="text"
            @click="githubClick()"
            >github</el-button
          >
          <el-button
            slot="reference"
            class="headClick"
            type="text"
            @click="openConsole()"
            style="padding-right: 10px"
            >控制台</el-button
          >
        </el-popover>
      </el-header>
      <el-container>
        <el-aside width="150px">
          <el-col>
            <!-- @select="handleSelect" -->
            <el-menu
              default-active="/project"
              class="el-menu-vertical-demo"
              router
            >
              <el-menu-item index="/project">
                <i class="el-icon-folder"></i>
                <span slot="title">项目</span>
              </el-menu-item>
              <el-menu-item index="/editor">
                <i class="el-icon-menu"></i>
                <span slot="title">编辑器</span>
              </el-menu-item>
              <el-menu-item index="/setting">
                <i class="el-icon-setting"></i>
                <span slot="title">设置</span>
              </el-menu-item>
            </el-menu>
          </el-col>
        </el-aside>
        <el-container>
          <el-main id="main"><router-view /></el-main>
        </el-container>
      </el-container>
    </el-container>
  </div>
</template>

<script>
export default {
  name: "Index",
  methods: {
    githubClick() {
      window.remote.shell.openExternal(
        "https://github.com/gameguo/cute_unity_launcher"
      );
    },
    openConsole() {
      this.common_event.openDevTools();
    },
  },
};
</script>

<style>
.contentContent .row-item {
  position: absolute;
  width: 100%;
  height: calc(100%);
}
.flexContainer {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;
  background-color: white;
}
.contentTitle {
  margin: 0;
  /* margin: 10px 10px 0px 10px; */
  height: 40px;
  background-color: white;
  padding: 2px 20px;
  text-align: left;
  line-height: 40px;
  font-size: 20px;
  overflow: hidden;
  text-overflow: ellipsis;
}
.contentContent {
  position: relative;
  flex: 1;
  display: flex;
  flex-direction: column;
  margin: 0;
  overflow: hidden;
}
.contentBottom {
  display: flex;
  flex-direction: row-reverse;
  align-items: center; /* 垂直居中 */
  margin: 10px;
  height: 40px;
  padding-right: 20px;
  background-color: white;
}
.contentBottomBtn {
  height: 35px;
  width: 100px;
  margin-right: 10px;
  text-align: center;
}

.el-header .headClick {
  float: right;
  height: 30px;
  color: #000000;
  overflow: hidden;
  text-align: center;
  text-overflow: ellipsis;
}
.el-header .headTitle {
  font-size: 15px;
  text-align: center;
  /* font-weight: 340; */
  color: #3b3b3b;
  line-height: 30px;
  white-space: nowrap;
  position: absolute;
  left: 20px;
  top: 0px;
  overflow: hidden;
  text-overflow: ellipsis;
}
.el-header img {
  height: 90%;
}
.el-header {
  /* border-radius: 30px; */
  box-shadow: 0 2px 12px rgba(0, 0, 0, 0.12), 0 0 6px rgba(0, 0, 0, 0.1);
  -webkit-app-region: drag;
  background-color: #ffffff;
  /* -webkit-app-region: drag; */
  z-index: 10;
}

.el-aside {
  background-color: #ffffff;
  text-align: left;
  box-shadow: 0 2px 12px rgba(224, 224, 224, 0.12),
    0 0 6px rgba(56, 56, 56, 0.1);
  z-index: 5;
}
.el-menu-item [class^="el-icon-"] {
  margin-left: 10px;
}

#main {
  background-color: #f2f3f4;
  text-align: center;
  padding: 0px;
}

#index,
.el-container {
  width: 100%;
  height: 100%;
}
</style>