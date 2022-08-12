<template>
  <div class="container">
    <TheMenu />
    <router-view> </router-view>
    <BaseToastMessage
      toastContent="Đăng nhập thành công"
      backgroundColor="#31B491"
      :isShow="true"
    >
      <div class="icon-accept"></div>
    </BaseToastMessage>
    
  </div>
</template>

<script>
import TheMenu from "./components/layout/TheMenu.vue";
import BaseToastMessage from "./components/base/BaseToastMessage.vue";

export default {
  name: "App",
  components: {
    TheMenu,
    BaseToastMessage,
  },
};
</script>

<style>
@import url("./style/font.css");
@import url("./style/icons.css");
@import url("./style/tooltip.css");
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@500&display=swap");
.container {
  display: flex;
  flex-direction: column;
}
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  font-family: Regular;
  overflow: hidden;
}
.mgr-8 {
  margin-right: 8px;
}
.container::-webkit-scrollbar-track {
  background-color: #f1f1f1 !important;
}
.container::-webkit-scrollbar-thumb:hover {
  background-color: #99a1b2 !important;
}
.container::-webkit-scrollbar-thumb {
  background-color: #c5c9d3 !important;
  border-radius: 4px !important;
}

.container::-webkit-scrollbar-thumb:active {
  background-color: #7c869c !important;
}
</style>
