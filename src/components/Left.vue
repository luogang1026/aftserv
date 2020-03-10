<template>
  <div class="left">
      <div class="user-info">
          <div class="user-info-bc"></div>
          <i class="el-icon-s-custom"></i>
          <div>admin/管理员</div>
      </div>
      <div class="manage" :class="{'color-4c4a55':menu=='user'}" @click="selectManage()"><i class="el-icon-user-solid"></i><span>用户管理</span></div>
      <div class="manage"><i class="el-icon-s-cooperation"></i><span>商品管理</span></div>
  </div>
</template>

<script>
export default {
    data(){
        return {
            menu:"user"
        }
    },
    methods:{
        selectManage(){
            // const self = this;
            this.$router.push("/user");
        }
    }

}
</script>

<style>
.left{
    /* height: 100%; */
    /* position: relative; */
    /* width:200px; */
    background-color: #34323d;
    color:#fff;
    height:100%;
    font-size:14px;
    /* padding:20px; */
}
.manage{
    padding:15px 30px;
    height:20px;
    line-height: 20px;
    /* background-color: #409eff; */
}
.color-4c4a55{
    background-color: #4c4a55;
}
span{
    margin-left:10px;
}
.user-info{
    padding:25px 30px;
    text-align:center;
    position: relative;
}
.user-info i{
    position: absolute;
    left: 86px;
    color:
    #34323d;
    top: 36px;
    font-size: 28px;
}
.user-info-bc{
    width:50px;
    height:50px;
    border-radius: 50px;
    background-color: #fff;
    margin-left:45px;
    margin-bottom: 10px;
}
</style>