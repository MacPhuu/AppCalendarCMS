<template>
  <q-header elevated class="bg-white flex items-center" style="height: 64px">
    <q-toolbar class="flex row reverse">
      <q-icon class="text-black" name="account_circle" size="30px" />
      <span class="text-black q-mx-md">Admin</span>
      <AddButton label="Thêm thành viên"></AddButton>
      <SearchBox
        style="margin-right: 15%; margin-left: 45px"
        placeholder="Tìm kiếm thành viên..."
      ></SearchBox>
    </q-toolbar>
  </q-header>
  <div class="q-ma-xl">
    <div class="breadscrum">
      <q-breadcrumbs>
        <q-breadcrumbs-el label="Thành viên" />
      </q-breadcrumbs>
    </div>

    <div class="separator"></div>
  </div>
  <MembershipTable />
</template>
<script>
import { defineComponent } from "vue";
import AddButton from "components/AddButton.vue";
import SearchBox from "components/SearchBox.vue";
import { usePagesStore } from "src/stores/pages";
import MembershipTable from "components/Membership/table.vue";

const PageStore = usePagesStore();

const data = [
  {
    Login_Name: "ABC",
    Name: "Nguyễn Văn A",
    Position: "Admin",
  },
  {
    Login_Name: "ABC1",
    Name: "Nguyễn Văn B",
    Position: "Member",
  },
  {
    Login_Name: "ABC2",
    Name: "Nguyễn Văn C",
    Position: "Member",
  },
];

const columns = [
  {
    name: "Index",
    label: "STT",
    field: "index",
    sortable: false,
    align: "left",
    headerStyle: "font-size: 17px",
    style: "font-size: 17px",
  },
  {
    name: "Login Name",
    label: "Tên đăng nhập",
    field: "Login_Name",
    sortable: true,
    align: "left",
    headerStyle: "font-size: 17px",
    style: "font-size: 17px",
  },
  {
    name: "Name",
    label: "Họ tên",
    field: "Name",
    sortable: true,
    align: "left",
    headerStyle: "font-size: 17px",
    style: "font-size: 17px",
  },
  {
    name: "Position",
    label: "Chức vụ",
    field: "Position",
    sortable: true,
    align: "left",
    headerStyle: "font-size: 17px",
    style: "font-size: 17px",
  },
  {
    name: "Action",
    label: "Thao tác",
    field: "Action",
    sortable: false,
    align: "center",
    headerStyle: "font-size: 17px",
    style: "font-size: 17px",
  },
];
let rows = [];
for (let i = 0; i < data.length; i++) {
  rows = data;
}
rows.forEach((row, index) => {
  row.index = index + 1;
});
export default defineComponent({
  name: "MembershipPage",
  components: {
    AddButton,
    SearchBox,
    MembershipTable,
  },

  created() {
    const Path = window.location.hash;
    for (var i of PageStore.pagesList) {
      if (Path.indexOf(i.direct) != -1) {
        i.active = true;
      } else i.active = false;
    }
  },
});
</script>
<style scoped>
.breadscrum {
  position: absolute;
  font-size: 17px;
  top: 100px;
  left: 267px;
  background-color: white;
  padding: 0 30px 0 30px;
}
.separator {
  border-bottom: 3px solid #e9eaec;
}
</style>
