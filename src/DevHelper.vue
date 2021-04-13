<template>
    <el-dialog title="我是开发小助手" :visible.sync="dialogFlag">
        <el-tabs>
           <el-tab-pane label="接口地址">
                <dev-helper-addapi  @confirm='confirm' 
                :listAPI='listAPI'
                :listsocketAPI='listsocketAPI'/>
            </el-tab-pane> 
            <el-tab-pane label="上传文件">
                <dev-helper-addfiles :loadpath='loadpath' @confirm='confirm'/>
            </el-tab-pane>
        </el-tabs>
    </el-dialog>
</template>

<script>
/*
* name:开发助手 
* author: gaoyanan
* Tue Apr 13 2021 14:51:19 GMT+0800
*/
export default {
  name: "DevHelper",
  props:{
    loadpath:'',
    listAPI:{},
    listsocketAPI:{}
  },
  components: { 
    DevHelperAddapi:()=>import('./DevHelper-addapi'),
    DevHelperAddfiles:()=>import('./DevHelper-addfiles'),
      },
  data() {
    return {
      dialogFlag: false,
      apiOptionsArr: []
    };
  },
  mounted() {
    console.log("********** 我是开发小助手(ctrl+s) ***********");
    console.log(this.loadpath);
    this.handlerKeyCommander();
  },
  methods: {
    /**
     * 键盘命令事件 (当前组件键盘: ctrl + 0)
     * @param {Event} e
     */
    handlerKeyCommander() {
      document.addEventListener("keydown", e => {
        var event = e || window.event;
        var keycode = event.keyCode || event.which || event.charCode || 0;
        var ctrlKey = event.ctrlKey || event.metaKey;
        // ctrl + s(number)
        if (ctrlKey && keycode === 83) {
          event.preventDefault();
          this.dialogFlag = true;
        }
      });
    },
    confirm(val){
      debugger
     this.dialogFlag=false
     val&&window.location.reload()
    }
  }
};
</script>