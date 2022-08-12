<template>
  <div class="sidebarright" id="sidebar-right">
    <div class="sidebarright-quick">
      <div class="button-quick" data-tooltip="Thêm cuộc gọi">
        <div class="icon-call"></div>
      </div>
      <div class="button-quick" data-tooltip="Thêm nhiệm vụ">
        <div class="icon-date"></div>
      </div>
      <div class="button-quick" data-tooltip="Thêm lịch hẹn">
        <div class="icon-birth"></div>
      </div>
      <div class="button-quick" data-tooltip="Gửi email">
        <div class="icon-email"></div>
      </div>
    </div>
    <div class="title-history">Lịch sử giao dịch</div>
    <div class="item-note">
      <div class="box-iconnote">
        <div class="icon-notebook"></div>
      </div>
      <div class="context-note">
        <div class="font-bold">Ghi chú</div>
        <div>Nguyễn Văn Hà (A006) - 12/08/2022</div>
      </div>
    </div>
    <div class="toolbar__right">
      <div class="icon-filter"></div>
    </div>
    <div class="collapse__right" id="sidebar-right" @click="hideSidebarRight">
      <div class="icon-collapse-right"></div>
    </div>
  </div>
  <div class="collapse__right--hide" id="collapse-right-hide" @click="showSidebarRight">
    <div class="icon-collapse-left"></div>
  </div>
</template>

<script>
export default {
  name: "TheSidebarRight",
  components: {

  },
  methods: {
    /**
     * Chức năng ẩn hiện sidebar
     * Author : DHTHINH(28/07/2022)
     */
    
    //Hàm ẩn sidebar
    hideSidebarRight() {
      document.getElementById("sidebar-right").style.display = "none";
      document.getElementById("collapse-right-hide").style.display = "flex";
    },
    //Hàm show sidebar
    showSidebarRight() {
      document.getElementById("sidebar-right").style.display = "block";
      document.getElementById("collapse-right-hide").style.display = "none";
    },
  },
};
</script>

<style>
.sidebarright {
  width: 319px;
  border-left: solid 1px #ccc;
  position: relative;
}
.collapse__right {
  display: flex;
  align-items: center;
  cursor: pointer;
  box-shadow: -2px 0 4px #00000029;
  border-radius: 6px 0 0 6px;
  background-color: #fff;
  z-index: 1;
  position: absolute;
  right: 320px;
  top: calc(50% - 20px);
  width: 12px !important;
  height: 40px !important;
  padding: 12px 0 !important;
}

.collapse__right--hide {
  display: none;
  align-items: center;
  cursor: pointer;
  box-shadow: -2px 0 4px #00000029;
  border-radius: 6px 0 0 6px;
  background-color: #fff;
  z-index: 1;
  position: absolute;
  right: 0;
  top: calc(50% + 50px);
  width: 12px !important;
  height: 40px !important;
  padding: 12px 0 !important;
}

.collapse__right:hover {
  width: 20px !important;
}

.collapse__right--hide:hover {
  width: 20px !important;
}

.sidebarright-quick {
  border-bottom: solid 1px #ccc;
  height: 40px;
  display: flex;
}

.button-quick {
  cursor: pointer;
  flex: 4;
  border: 0;
  background-color: #fff;
  display: flex;
  align-items: center;
  justify-content: center;
}
.button-quick:hover {
  background-color: #f0f2f4;
}
.title-history {
  font-family: Roboto;
  font-size: 16px;
  padding: 16px;
  display: flex;
  color: #1f2229;
}

.item-note {
  display: flex;
  padding: 0 16px 12px;
}

.item-note:hover {
  background-color: #f0f2f4;
}

.context-note {
  cursor: pointer;
  font-size: 13px;
  padding-left: 8px;
}
.font-bold {
  font-family: Bold;
}
.box-iconnote {
  width: 28px;
  height: 28px;
  background-color: #2ec2fc;
  border-radius: 50%;
}
.toolbar__right {
  cursor: pointer;
  position: absolute;
  right: 16px;
  bottom: 16px;
  padding: 8px;
  border-radius: 50%;
  box-shadow: 0 2px 4px 1px #0000003d;
}
.toolbar__right:hover {
 background-color: #f0f2f4;
}
</style>