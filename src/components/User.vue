<template>
  <div class="user">
    <div class="user-title">用户管理</div>
    <div>
      <el-table :data="tableData" style="width: 100%">
        <el-table-column prop="date" label="账户" width="180"></el-table-column>
        <el-table-column prop="name" label="推荐人" width="180"></el-table-column>
        <el-table-column prop="name" label="当前单量" width="180"></el-table-column>
        <el-table-column prop="name" label="总收益" width="180"></el-table-column>
        <el-table-column prop="address" label="账号状态"></el-table-column>
        <el-table-column label="操作">
          <template slot-scope="scope">
            <el-button size="mini" @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
            <el-button size="mini" type="danger" @click="handleDelete(scope.$index, scope.row)">删除</el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tableData: [
      ]
    };
  },
  mounted:function() {
    this.userList()
  },
  methods: {
    userList() {
      const that = this;
      //   that.$router.push({path:"/main/user"});
      if (!that.username) {
        that.error = "请输入用户名";
        return;
      }
      if (!that.password) {
        that.error = "请输入密码";
        return;
      }

      that.$axios
        .post("/api/user/coupon/accountlist", {
          pageSize: 10,
          curPage: 1
        })
        .then(function(response) {
          console.log(response);
          const data = JSON.parse(response.data);
          console.log(data);
          if (data.errno === 0) {
            sessionStorage.setItem("tableData", that.data.list);
            that.$router.push({ path: "/main/user" });
          } else {
            that.error = data.errmsg;
          }
        })
        .catch(function(error) {
          console.log(error);
        });
    }
  }
};
</script>

<style>
.user {
  padding: 30px;
}
.user-title {
  height: 34px;
  line-height: 34px;
}
.el-table th{
    background-color: #f2f1f6 !important;
}
</style>