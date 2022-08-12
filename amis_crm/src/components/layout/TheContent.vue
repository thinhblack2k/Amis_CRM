<template>
  <div class="content">
    <!-- <BaseToggle switchText="Switch" />
        <BaseToggle switchText="Switch Disabled" :switchDisabled="true"/> -->
    <div class="content__table">
      <table class="table">
        <thead>
          <tr>
            <th class="icon__setcolumn" style="width: 46px">
              <div class="btn-settings-column icon-sticky-setting-column">
                <span class="icon-add_colums_16"></span>
              </div>
            </th>
            <th class="text-align-center" style="width: 40px">
              <BaseCheckbox name="" id="" :hasLable="false" />
            </th>
            <th style="width: 150px" class="text-align-left">Thẻ</th>
            <th class="text-align-left" style="width: 120px">Xưng hô</th>
            <th class="text-align-left" style="width: 250px">Họ và tên</th>
            <th class="text-align-left" style="width: 180px">Chức danh</th>
            <th class="text-align-left" style="width: 150px">ĐT di động</th>
            <th class="text-align-left" style="width: 150px">ĐT cơ quan</th>
            <th class="text-align-left" style="width: 250px">Email cơ quan</th>
            <th class="text-align-left" style="width: 250px">Email cá nhân</th>
            <th class="text-align-left" style="width: 150px">Tổ chức</th>
            <th class="text-align-left" style="width: 150px">Địa chỉ</th>
            <th class="text-align-left" style="width: 150px">Tỉnh/Thành phố</th>
            <th class="text-align-left" style="width: 150px">Quận/Huyện</th>
            <th class="text-align-left" style="width: 150px">Phường/Xã</th>
            <th class="text-align-left" style="width: 150px">Nguồn gốc</th>
            <th class="text-align-left" style="width: 150px">Loại hình</th>
            <th class="text-align-left" style="width: 150px">Lĩnh vực</th>
            <th class="text-align-left" style="width: 150px">Mô tả</th>
            <th class="text-align-left" style="width: 150px">Bố cục</th>
            <th class="text-align-left" style="width: 150px">Chủ sở hữu</th>
            <th class="text-align-left" style="width: 150px">Dùng chung</th>
            <th class="text-align-left" style="width: 150px">Zalo</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in leads" :key="item.LeadID">
            <td><div class="icon-edit icon-pen"></div></td>
            <th class="text-align-center">
              <BaseCheckbox name="" id="" :hasLable="false" />
            </th>
            <td class="text-align-left"></td>
            <td class="text-align-left">{{ formatData(item.salutationName) }}</td>
            <td class="text-align-left text--blue">
              {{ item.lastName + " " +item.firstName }}
            </td>
            <td class="text-align-left">{{ formatData(item.titleName) }}</td>
            <td class="text-align-left text--blue">
              <div class="text--icon">
                <div class="icon-telephone"></div>
                <div>{{ formatData(item.mobile) }}</div>
              </div>
            </td>
            <td class="text-align-left text--blue">
              <div class="text--icon">
                <div class="icon-telephone"></div>
                <div>{{ formatData(item.officeMobile) }}</div>
              </div>
            </td>
            <td class="text-align-left text--blue">
              {{ formatData(item.email) }}
            </td>
            <td class="text-align-left text--blue">
              {{ formatData(item.officeEmail) }}
            </td>
            <td class="text-align-left">{{ formatData(item.street) }}</td>
            <td class="text-align-left">{{ formatData(item.sectorName)}}</td>
            <td class="text-align-left">{{ formatData(item.address) }}</td>
            <td class="text-align-left">{{ formatData(item.districtName) }}</td>
            <td class="text-align-left">{{ formatData(item.wardName) }}</td>
            <td class="text-align-left">{{ formatData(item.leadSourceName) }}</td>
            <td class="text-align-left">{{ formatData(item.leadTypeName) }}</td>
            <td class="text-align-left">{{ formatData(item.industryName) }}</td>
            <td class="text-align-left">{{ formatData(item.description) }}</td>
            <td class="text-align-left">{{ formatData(item.zipCode) }}</td>
            <td class="text-align-left">{{ formatData(item.createdBy) }}</td>
            <td class="text-align-left">{{ formatData(item.isPublic) }}</td>
            <td class="text-align-left">{{ formatData(item.zalo) }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="navigate">
      <div class="navigate__left">
        <div class="ic-sort-setting border-icon">
          <div class="icon-sortsetting"></div>
        </div>
        Tổng số: <span class="text--bold" style="margin-left: 8px"> 820</span>
      </div>
      <div class="navigate__right">
        <div class="page__size">
          <BaseDropDown
            :arrays="PAGESIZE"
            dropdownContent="20 Bản ghi trên trang"
          />
        </div>
        <div class="page__list">
          <div class="page__item">
            <div class="icon-pre2"></div>
          </div>
          <div class="page__item">
            <div class="icon-pre1"></div>
          </div>
          <div class="navigate__text" style="font-weight: 500">
            <span class="text--bold">1</span>
            <span style="padding: 0 8px">đến</span>
            <span class="text--bold">20</span>
          </div>
          <div class="page__item">
            <div class="icon-next1"></div>
          </div>
          <div class="page__item">
            <div class="icon-next2"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PAGESIZE from "../../constants/PageSize";
import BaseDropDown from "../base/BaseDropDownMenu.vue";
import BaseCheckbox from "../base/BaseCheckbox.vue";
import axios from "axios";
export default {
  name: "TheContent",
  components: {
    BaseDropDown,
    BaseCheckbox,
  },

  //http://localhost:5245/api/v1/Leads
  //https://cukcuk.manhnv.net/api/v1/Employees
  created() {
    try {
      var temp = this;
      axios
        .get("http://localhost:5245/api/v1/Leads")
        .then(function (res) {
          console.log(res);
          temp.leads = res.data;
        })
        .catch(function (err) {
          console.log(err);
        });
    } catch (error) {
      console.log(error);
    }
  },
  data() {
    return {
      PAGESIZE,
      leads: null,
    };
  },
  methods: {
    formatData(text) {
      if (text == null || text == "") {
        text = "-";
      }
      return text;
    },
    formatGender(gender) {
      let vocative = "Anh";
      if (gender == 0) {
        vocative = "Anh";
      } else if (gender == 1) {
        vocative = "Chị";
      }
      else {
        vocative = "Chưa xác định"
      }
      return vocative;
    },
  },
};
</script>

<style>
@import url(../../style/table.css);
@import url(../../style/navigate.css);
.btn-settings-column {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 24px;
  height: 24px;
}
.icon-sticky-setting-column {
  z-index: 1001;
  top: 9px;
  right: 2px;
  background-color: #fff;
  border-radius: 50%;
  width: 24px;
  height: 24px;
  /* overflow: hidden; */
  box-shadow: 0 2px 6px #00000052;
}

.icon-sticky-setting-column:hover {
  background-color: #d3d7de;
  border-radius: 50%;
}

.icon-add_colums_16 {
  display: inline-block;
  cursor: pointer;
  vertical-align: middle;
  width: 16px;
  height: 16px;
  background: url("../../assets/Resource/img/icon_collection.svg") no-repeat 0 0;
}

.content {
  flex: 1;
  position: relative;
}

.icon__setcolumn {
  padding: 0 10px 0 12px;
  width: 30px;
}

.icon-edit {
  display: none;
  margin-left: 14px;
}

.table tr:hover .icon-edit {
  display: block;
}
</style>