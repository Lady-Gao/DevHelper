<template>
   <el-form>
     <el-form-item>
       <span v-show='devUrl'>
          IP :
     <el-select v-model="devApi" style='margin-right:20px' >
       <el-option v-for="item in listAPI.list" :key='item.label' :label="item.label" :value='item.value'></el-option>
     </el-select>
       </span>
    <span v-show='socketUrl' >
       Socket :
     <el-select v-model="socketApi" >
       <el-option v-for="item in listsocketAPI.list" :key='item.label' :label="item.label" :value='item.value'></el-option>
     </el-select>
      </span>
     </el-form-item>
     <el-form-item>
     	<el-button type="primary"   @click="handlerForm">{{ $t('action.confirm') }}</el-button>
     </el-form-item>
   </el-form>
</template>

<script>
export default {
  props:{
    listAPI:{},
    listsocketAPI:{}
  },
  computed:{
    devUrl(){
      return this.listAPI.defaultUrl
    },
    socketUrl(){
      return this.listsocketAPI.defaultUrl
    },
  },
  data() {
    return {
      devApi:localStorage.getItem("dev-Api")||this.devUrl,
      socketApi:localStorage.getItem('socket-Api')||this.socketUrl
    };
  },
  methods: {
    handlerForm() {
     this.devApi&&localStorage.setItem('dev-Api',this.devApi)
     this.socketApi&&localStorage.setItem('socket-Api',this.socketApi)
     this.$emit('confirm',true)
    }
  }
};
</script>
<style>
</style>
