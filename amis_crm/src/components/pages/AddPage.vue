<template>
  <div class="function set-height">
    <div class="function__left">
      <h1 class="function__title" style="margin-right: 16px">Thêm Tiềm năng</h1>
      <div style="font-family: Roboto; font-size: 16px; padding-top: 4px">
        Mẫu tiêu chuẩn
      </div>
      <div class="function__edit" style="padding-top: 4px">Sửa bố cục</div>
    </div>
    <div class="layout__center"></div>
    <div class="function__right">
      <router-link class="link-router" to="/">
        <BaseButton
          class="mgr-8"
          :hasContent="true"
          buttonContent="Hủy bỏ"
          color="#000"
          backgroundColor="#fff"
          backgroundColorHover="#f0f2f4"
          borderColor="#d3d7de"
          :hasOutLined="true"
        />
      </router-link>
      <BaseButton
        class="mgr-8"
        :hasContent="true"
        buttonContent="Lưu và thêm"
        color="#4262F0"
        :hasOutLined="true"
        backgroundColor="#fff"
        borderColor="#4262F0"
        backgroundColorHover="#f0f2f4"
        @click="btnSaveAndAdd"
      />
      <BaseButton
        class="mgr-8"
        :hasContent="true"
        buttonContent="Lưu"
        color="#fff"
        backgroundColor="#4262F0"
        :hasOutLined="false"
        @click="btnSaveAndAdd"
      />
    </div>
  </div>
  <div class="potential-content">
    <div class="image-potential">
      <div class="image__title">Ảnh tiềm năng</div>
      <div class="image__content">
        <div class="icon__avatar"></div>
      </div>
    </div>
    <div class="main__potential">
      <div class="main__title">Thông tin chung</div>
      <div class="main__content">
        <div class="content__col" style="margin-right: 80px">
          <div class="content__row">
            <div class="content__title">Xưng hô</div>
            <div class="content__input">
              <BaseDropDown
                ref="cbxSalutationName"
                :propText="text"
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                :arrays="ListVocative"
                color="#1f2229"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">
              Tên <span style="color: red"> *</span>
            </div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
                idInput="txtName"
                ref="txtFirstName"
                :error="error['FirstName']"
                v-model="txtFirstName"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Phòng ban</div>
            <BaseDropDown
              ref="cbxDepartmentName"
              dropdownContent="-Không chọn-"
              :hasInputSearch="true"
              :arrays="ListDepartment"
              color="#1f2229"
            />
          </div>
          <div class="content__row">
            <div class="content__title">ĐT di động</div>
            <div class="content__input">
              <BaseTextField
                ref="txtMobile"
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Email cơ quan</div>
            <div class="content__input">
              <BaseTextField
                ref="OfficeEmail"
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Mã số thuế</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
                ref="LeadsCode"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Nguồn gốc</div>
            <div class="content__input">
              <BaseDropDown
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Zalo</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Phân loại Khách hàng</div>
            <div class="content__input">
              <BaseDropDown
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Loại học bổng</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Điểm HSKK</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Điểm HSK</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title" style="padding-bottom: 45px">
              Chia sẻ cá nhân
            </div>
            <div class="content__input">
              <BaseTextArea placeholder="" />
            </div>
          </div>
        </div>
        <div class="content__col">
          <div class="content__row">
            <div class="content__title">Họ và tên</div>
            <div class="content__input">
              <BaseTextField
                ref="txtFullName"
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
                :readOnly="true"
                :modelValue="txtLastName+txtSpace+txtFirstName"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Họ và đệm</div>
            <div class="content__input">
              <BaseTextField
                ref="txtLastName"
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
                v-model="txtLastName"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Chức danh</div>
            <div class="content__input">
              <BaseDropDown
                ref="TitleName"
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">ĐT cơ quan</div>
            <div class="content__input">
              <BaseTextField
                ref="OfficeMobile"
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Email cá nhân</div>
            <div class="content__input">
              <BaseTextField
                ref="Email"
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Tổ chức</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Mã ngân sách</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Quy mô</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Học vấn hiện tại</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Trường học</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Hình thức mong muốn</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title" style="padding-bottom: 45px">Hồ sơ</div>
            <div class="content__input">
              <BaseTextArea placeholder="" />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Thời gian dự định du học</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">
              Test chuyển đổi <span style="color: red"> *</span>
            </div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
                idInput="txtTestChange"
                ref="TestChange"
                :error="error['TestChange']"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="main__potential">
      <div class="main__title">Thông tin tổ chức</div>
      <div class="main__content">
        <div class="content__col" style="margin-right: 80px">
          <div class="content__row">
            <div class="content__title">Tài khoản ngân hàng</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
                :typeInput="date"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Ngày thành lập</div>
            <div class="content__input">
              <BaseDatePicker backgroundColor="#fff" />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Lĩnh vực</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Doanh thu/ Ngân sách</div>
            <div class="content__input">
              <BaseDropDown
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
        </div>
        <div class="content__col">
          <div class="content__row">
            <div class="content__title">Mở tại ngân hàng</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Loại hình</div>
            <div class="content__input">
              <BaseDropDown
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Ngành nghề</div>
            <div class="content__input">
              <BaseDropDown
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="main__potential">
      <div class="main__title">Thông tin địa chỉ</div>
      <div class="main__content">
        <div class="content__col" style="margin-right: 80px">
          <div class="content__row">
            <div class="content__title">Quốc gia</div>
            <div class="content__input">
              <BaseDropDown
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Quận/huyện</div>
            <div class="content__input">
              <BaseDropDown
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Số nhà, Đường phố</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
                ref="Address"
                :error="error.address"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title" style="padding-bottom: 45px">
              Địa chỉ
            </div>
            <div class="content__input">
              <BaseTextArea textContent="" placeholder="" />
            </div>
          </div>
        </div>
        <div class="content__col">
          <div class="content__row">
            <div class="content__title">Tỉnh/Thành phố</div>
            <div class="content__input">
              <BaseDropDown
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Phường/Xã</div>
            <div class="content__input">
              <BaseDropDown
                dropdownContent="-Không chọn-"
                :hasInputSearch="true"
                color="#1f2229"
              />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Mã vùng</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="main__potential">
      <div class="main__title">Thông tin mô tả</div>
      <div class="main__content">
        <div class="content__col">
          <div class="content__row">
            <div class="content__title" style="padding-bottom: 45px">Mô tả</div>
            <div class="content__input">
              <BaseTextArea textContent="" placeholder="" />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="main__potential">
      <div class="main__title">Thông tin hệ thống</div>
      <div class="main__content">
        <div class="content__col">
          <div class="content__row">
            <div class="content__title">Dùng chung</div>
            <div class="content__input">
              <BaseCheckbox filterContent="" />
            </div>
          </div>
          <div class="content__row">
            <div class="content__title">Mã tiềm năng</div>
            <div class="content__input">
              <BaseTextField
                backgroundColor="#fff"
                :hasBorder="true"
                width="100%"
              />
            </div>
          </div>
        </div>
        <div class="content__col"></div>
      </div>
    </div>
    <BasePopup :hasShowPopup="false" popupContent="" />
  </div>
</template>

<script>
import { ref } from "vue";
import LIST_DEPARTMENT from "../../constants/ListDepartment";
import LIST_VOCATIVE from "../../constants/ListVocative";
import BaseButton from "../base/BaseButton.vue";
import BaseCheckbox from "../base/BaseCheckbox.vue";
import BaseDatePicker from "../base/BaseDatePicker.vue";
import BaseDropDown from "../base/BaseDropDown.vue";
import BaseTextArea from "../base/BaseTextArea.vue";
import BaseTextField from "../base/BaseTextField.vue";
import BasePopup from "../base/BasePopup.vue";
import axios from "axios";

export default {
  name: "TheFunction",
  components: {
    BaseButton,
    BaseDropDown,
    BaseTextField,
    BaseTextArea,
    BaseDatePicker,
    BaseCheckbox,
    BasePopup,
  },
  data() {
    return {
      lead: [],
      error: {
        SalutationName: "",
        address: "",
        FullName: "",
        FirstName: "",
        DepartmentName: "",
        LastName: "",
        Mobile: "",
        OfficeMobile: "",
        TitleName: "",
        Email: "",
        OfficeEmail: "",
        LeadsCode: "",
      },
      leadCodeNew: null,
      txtFirstName: "",
      txtLastName: "",
      txtSpace: " ",
    };
  },
  created() {
    try {
      var temp = this;
      axios
        .get("http://localhost:5245/api/v1/Leads/NewLeadCode")
        .then(function (res) {
          console.log(res);
          temp.leadCodeNew = res.data;
        })
        .catch(function (err) {
          console.log(err);
        });
    } catch (error) {
      console.log(error);
    }
  },
  setup() {
    const ListVocative = ref(LIST_VOCATIVE);
    const ListDepartment = ref(LIST_DEPARTMENT);

    return {
      ListVocative,
      ListDepartment,
    };
  },
  /**
     * created (setup)
     */
  methods: {
    btnSaveAndAdd() {
      //Build object thông tin nhân viên
      const Lead = {};
      Lead["SalutationName"] = this.$refs.cbxSalutationName.value;
      Lead["FirstName"] = this.$refs.txtFirstName.value;
      Lead["LastName"] = this.$refs.txtLastName.value;
      Lead["TestChange"] = this.$refs.TestChange.value;
      Lead["DepartmentName"] = this.$refs.cbxDepartmentName.value;
      Lead["TitleName"] = this.$refs.TitleName.value;
      Lead["Mobile"] = this.$refs.txtMobile.value;
      Lead["OfficeMobile"] = this.$refs.OfficeMobile.value;
      Lead["OfficeEmail"] = this.$refs.OfficeEmail.value;
      Lead["Email"] = this.$refs.Email.value;
      Lead["LeadsCode"] = this.$refs.LeadsCode.value;

      // Lead[""] = this.$refs..value;
      // Lead[""] = this.$refs..value;
      // Lead[""] = this.$refs..value;
      // Lead[""] = this.$refs..value;
      // Lead[""] = this.$refs..value;
      console.log(Lead);

      //Validate dữ liệu:
      for (const key in Lead) {
        if (
          key == "SalutationName" ||
          key == "FirstName" ||
          key == "TestChange"
        ) {
          if (Lead[key] == "")
            this.error[key] = "Thông tin này không được phép để trống";
        } else {
          this.error[key] = "";
        }
      }
      
      //Gọi api thực hiện thêm mới
      try {
      axios
        .post("http://localhost:5245/api/v1/Leads", Lead)
        .then(function () {
          console.log();
          alert("Thêm mới thành công")
        })
        .catch((res) => {
          console.log(res)
        });
    } catch (error) {
      console.log(error);
    }
    },
  },
};
</script>

<style>
.set-height {
  height: 62px;
}

.function {
  width: 100%;
  z-index: 1;
}

.function__left {
  display: flex;
  align-items: center;
}

.function__title {
  margin-left: 16px;
  font-size: 20px;
  font-weight: 500;
  font-family: Roboto;
  line-height: 1.428571429;
  color: #1f2229;
}

.function__edit {
  margin-left: 8px;
  color: #5973eb;
  font-size: 13px;
}

.layout__center {
  flex: 1;
}

.function__right {
  display: flex;
  margin-right: 8px;
}

.link-router {
  text-decoration: none;
}

.potential-content {
  padding: 38px 0 0;
  grid-column-start: 1;
  grid-column-end: 5;
  font-family: Roboto;
  overflow-y: auto;
  height: calc(100vh - 125px);
}

.image-potential {
  margin: 0px 56px 40px 56px;
}

.image__title {
  margin-bottom: 16px;
  font-size: 18px;
}

.image__content {
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  width: 48px;
  height: 48px;
  background-color: #f0f2f4;
  border-radius: 50%;
  margin: 16px 0 40px 0;
}

.icon__avatar {
  content: "";
  display: inline-block;
  width: 48px;
  height: 48px;
  border-radius: -50%;
  background: transparent
    url(https://crmplatform.misacdn.net/app/assets/Images/icon/icon_collection.svg)
    no-repeat -144px -848px;
}
.icon__avatar:hover {
  display: inline-block;
  width: 40px;
  height: 40px;

  background: transparent
    url(https://crmplatform.misacdn.net/app/assets/Images/icon/icon_collection.svg)
    no-repeat -200px -808px;
}

.main__potential {
  margin-bottom: 20px;
}

.main__title {
  margin: 0 56px 4px;
  font-size: 18px;
}

.main__content {
  display: flex;
  flex-direction: row;
  padding: 8px 56px;
}

.content__col {
  display: flex;
  flex-direction: column;
  flex: 1;
}

.content__row {
  display: flex;
  padding: 4px 0;
  margin: 2px 0px;
  align-items: center;
}

.content__title {
  width: 160px;
  font-size: 13px;
  flex-shrink: 0;
  color: #454545;
  font-weight: 400;
}

.content__input {
  width: 100%;
}
</style>