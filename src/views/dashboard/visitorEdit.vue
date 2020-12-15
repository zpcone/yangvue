<!--  -->
<template>
    <div class='' style="margin-top:50px;">
      <el-form ref="form" :model="sizeForm" label-width="80px">
        <el-form-item label="店铺名称">
          <el-select v-model="sizeForm.shopName" style="width:300px;" placeholder="请选择店铺">
            <el-option label="jimmy店" value="1"></el-option>
            <el-option label="机灵店" value="2"></el-option>
            <el-option label="上官店" value="3"></el-option>
            <el-option label="南宫店" value="4"></el-option>
          </el-select>
        </el-form-item>
        <el-form-item label="旺旺账号">
          <el-input v-model="sizeForm.wangNum"  style="width:300px" placeholder="请输入旺旺账号"></el-input>
        </el-form-item>
        <el-form-item label="已购产品">
          <el-input v-model="sizeForm.buyGood"  style="width:300px" placeholder="请输入已购产品"></el-input>
        </el-form-item>
        <el-form-item label="备注">
          <el-input v-model="sizeForm.beizhu"  style="width:300px" placeholder="请输入备注信息"></el-input>
        </el-form-item>
        <el-form-item label="时间">
           <el-date-picker
           style="width:300px"
            v-model="value2"
            type="datetime"
            placeholder="选择日期时间"
            align="right"
            :picker-options="pickerOptions">
          </el-date-picker>
        </el-form-item>
        <el-form-item size="large">
          <el-button type="primary" @click="onSubmit">保存</el-button>
          <el-button>重置</el-button>
        </el-form-item>
      </el-form>

    </div>
</template>

<script>
 //api文档自动生成模板
 /**
    * @api {get} /user/:id Request User information
    * @apiName GetUser
    * @apiGroup User
    *
    * @apiParam {Number} id Users unique ID.
    *
    * @apiSuccess {String} firstname Firstname of the User.
    * @apiSuccess {String} lastname  Lastname of the User.
    */
    
export default {
    
    components: {},
    data() {
        
        return {
          sizeForm: {
            wangNum: '',
            shopName: '',
            buyGood: '',
            beizhu: '',
            delivery: false,
            type: [],
            resource: '',
            desc: ''
          }
            
        };
    },
    //监听属性 类似于data概念
    computed: {},
    //监控data中的数据变化
    watch: {},
    
    methods: {
      onSubmit() {
        console.log('submit!');
      }
    },
    //生命周期 - 创建完成（可以访问当前this实例）
    created() {
        
    },
    //生命周期 - 挂载完成（可以访问DOM元素）
    mounted() {
      console.log(this.$route.query.id)
    },
    beforeCreate() {}, 
    beforeMount() {},
    beforeUpdate() {}, 
    updated() {}, 
    beforeDestroy() {}, 
    destroyed() {}, 
    //如果页面有keep-alive缓存功能，这个函数会触发
    activated() {}, 
    }
</script>
<style lang='scss' scoped>
    //@import url(); 引入公共css类
    
</style>