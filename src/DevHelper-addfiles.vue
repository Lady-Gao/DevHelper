<template>
  <div class='devhepler'>
    <el-popover ref="popover">
      <el-input placeholder="hello" />
    </el-popover>
    <el-row class="picture-upload">
      <el-col>
        <el-upload
          class="upload-dev"
          drag
          ref='loads'
           :action="loadpath"
          :before-upload="beforeImageUpload"
          :on-success='success'
           :data="{token: 'a1e941da1ad0828b01cef98b1a578f9f',hashFileName:false}"
        >
          <i class="el-icon-upload"></i>
          <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
        </el-upload>
      </el-col>
    </el-row>
  </div>
</template>

<script>

export default {
  props:{
    loadpath:''
  },
  data() {
    return {
    };
  },

  methods: {
    /**
     * 上传图片之前的回调
     * @param {Object} file: 上传内容的信息
     * @return {Boolean} 是否符合上传规则
     */
    beforeImageUpload(file) {
      const isIMG = [
        "image/jpeg",
        "image/png",
        "image/svg",
        "image/gif",
      ].indexOf(file.type);
      const isSIZE = file.size / 1024 / 1024 < 2;
      const isFile = file.size / (1024 * 1024) < 10;
      if (isIMG === -1) {
        if (!isFile) {
          Message.error("上传内容不能超过10M");
          return false;
        }
      } else {
        if (!isSIZE) {
          Message.error("上传内容不能超过2M");
          return false;
        }
      }
    },
    success(){
      setTimeout(() => {
         this.$emit('confirm')
      }, 1000);
    }
  },
};
</script>
<style lang="scss" scoped>

.upload-dev{
    margin-left: 100px ;
    margin-top: 40px ;
    margin-bottom: 40px ;
}
</style>
