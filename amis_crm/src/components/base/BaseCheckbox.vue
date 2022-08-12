<template>
  <div class="base-checkbox">
    <input type="checkbox" class="checkbox" :id="`checkbox--${filterId}`"/>
    <label v-if="isLable" class="title-checkbox" :for="`checkbox--${filterId}`">{{filterContent}}</label>
  </div>
</template>

<script>
export default {
  name: "BaseCheckbox",
  components: {},
  props: {
    filterId: {
      type: String,
    },
    filterContent: {
      type: String,
      default: "CheckBox",
    },
    //thiết lập trạng thái ban đầu có checked không
    checked: {
      type: Boolean,
      default: false,
    },
    //có lable không
    hasLable: {
      type: Boolean,
      default: true,
    }
  },
  computed: {
    /**
     * Thiết lập trang trạng thái checkbox
     * Author: DHTHINH (18/07/2022)
     */
    isLable() {
      return this.hasLable ? true : false;
    }
  },
};
</script>

<style scoped>
.base-checkbox {
  display: flex;
  padding: 8px 0px;
}

.base-checkbox span {
  cursor: pointer;
}

.checkbox {
  appearance: none;
  cursor: pointer;
  width: 16px;
  height: 16px;
  border-radius: 4px;
  margin: 0px;
  border: 1px solid #7c869c;
}

.checkbox:hover {
  border: 1px solid #2b4eee;;
}

.checkbox:checked {
  color: #fff;
  width: 16px;
  height: 16px;
  cursor: pointer;
  background: transparent url(../../assets/Resource/img/icon_collection.svg)
    no-repeat -176px -16px;
  border: none;
}

.title-checkbox {
  cursor: pointer;
  font-family: Regular;
  font-size: 13px;
  padding-left: 8px;
  flex: 1;
}
</style>