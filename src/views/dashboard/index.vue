<template>
  <div class="dashboard-editor-container">

    <el-form :inline="true" :model="formInline" class="demo-form-inline">
      <el-form-item label="店铺名称">
        <el-select v-model="formInline.shopName" placeholder="活动区域">
          <el-option label="jimmy店" value="1"></el-option>
          <el-option label="机灵点" value="2"></el-option>
          <el-option label="南宫店" value="3"></el-option>
          <el-option label="上官店" value="4"></el-option>
        </el-select>
      </el-form-item>
      <el-form-item label="客户姓名">
        <el-input v-model="formInline.userName" placeholder="姓名"></el-input>
      </el-form-item>
      <el-form-item label="旺旺号码">
        <el-input v-model="formInline.wanghao" placeholder="旺旺号"></el-input>
      </el-form-item>
      <el-form-item label="产品">
        <el-input v-model="formInline.goodsName" placeholder="已购产品"></el-input>
      </el-form-item>
   
      <el-form-item>
        <el-button plain type="primary" @click="onSearchSubmit">查询</el-button>
        <el-button plain type="primary" style="color:red;" @click="onAddSubmit">添加</el-button>
      </el-form-item>
    </el-form>


       <el-table
        :data="tableData"
        style="width: 100%">
        <!-- <el-table-column
          label="日期"
          width="180">
          <template slot-scope="scope">
            <i class="el-icon-time"></i>
            <span style="margin-left: 10px">{{ scope.row.date }}</span>
          </template>
        </el-table-column> -->
        <el-table-column
          type="index"
          label="序号"
          width="180">
        </el-table-column>

        <el-table-column
          prop="name"
          label="姓名"
          width="180">
        </el-table-column>

        <el-table-column
          prop="wangNum"
          label="旺旺账号"
          width="180">
        </el-table-column>

       

        <el-table-column
          label="已购产品"
          prop="buyGood"
          width="180">
        </el-table-column>

        <el-table-column
          label="售后备注"
          prop="wait"
          width="180">
        </el-table-column>

        <el-table-column label="操作">
          <template slot-scope="scope">
            <el-button
              size="mini"
              @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
            <el-button
              size="mini"
              type="danger"
              @click="handleDelete(scope.$index, scope.row)">删除</el-button>
          </template>
        </el-table-column>
      </el-table>

  </div>
</template>

<script>


export default {
  name: 'DashboardAdmin',
  data() {
    return {
      formInline: {
        userName: '',
        wanghao: '',
        goodsName:'',
        shopName:''
      },
         tableData: [{
          date: '2016-05-02',
          name: '王小虎',
          wangNum:'jdhdghdjklhkljhljlh',
          address: '上海市普陀区金沙江路 1518 弄',
          buyGood:'江南系列',
          wait:'发回北京'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          wangNum:'jdhdghdjklhkljhljlh',
          address: '上海市普陀区金沙江路 1517 弄',
          buyGood:'江南系列',
          wait:'发回北京'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          wangNum:'jdhdghdjklhkljhljlh',
          address: '上海市普陀区金沙江路 1519 弄',
          buyGood:'江南系列',
          wait:'发回北京'
        }, {
          date: '2016-05-03',
          name: '王小虎',
          wangNum:'jdhdghdjklhkljhljlh',
          address: '上海市普陀区金沙江路 1516 弄',
          buyGood:'江南系列',
          wait:'发回北京'
        }]
      // lineChartData: lineChartData.newVisitis
    }
  },
  created(){
    // console.log(this.$store.state.user.username)
    this.getAllGuest()
  }, 
  methods: {
    getAllGuest(){
       this.$axios({
        method: "get",
        url: "/guest/getAllGuest",
        withCredentials: true
      })
        .then((res) => {

        })
    },
    // 添加
    onAddSubmit(){
      if(!this.formInline.shopName){
        this.$message({
          message: '请先选择店铺',
          type: 'warning'
        });
      }
    },
    // 查询
    onSearchSubmit() {
      if(!this.formInline.shopName){
        this.$message({
          message: '请先选择店铺',
          type: 'warning'
        });
      }
    },
    handleEdit(index, row) {
        console.log(index, row);
        this.$router.push({ path: 'visitorEdit',query:{id:'1'}})
      },
      handleDelete(index, row) {
        var obj = {}
        obj.username = 'zpc'
        this.$axios({
          method:'post',
          url:'http://192.168.0.102:3000/ceshi',
          data:obj
          }).then((response) =>{          //这里使用了ES6的语法
              console.log(response)       //请求成功返回的数据
          })
        console.log(index, row);
      }
  }
}
</script>

<style lang="scss" scoped>
.dashboard-editor-container {
  padding: 32px;
  background-color: rgb(240, 242, 245);
  position: relative;

  .github-corner {
    position: absolute;
    top: 0px;
    border: 0;
    right: 0;
  }

  .chart-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;
  }
}

@media (max-width:1024px) {
  .chart-wrapper {
    padding: 8px;
  }
}
</style>
