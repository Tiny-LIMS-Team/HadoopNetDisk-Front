<template>
  <div>
    <h1>文件传输</h1>
    <div style="margin-top: 50px; margin-left: 50px">
      <el-upload
        class="upload-demo"
        drag
        action="https://jsonplaceholder.typicode.com/posts/"
        multiple
        :headers="headers"
        :on-change="loadFile"
        :auto-change="headleChange"
      >
        <i class="el-icon-upload"></i>
        <div class="el-upload__text">将文件拖到此处，或<em>点击上传</em></div>
        <div class="el-upload__tip" slot="tip">请勿上传1G以上的文件</div>
      </el-upload>
      <el-button @click="submit">上传</el-button>
    </div>
    <!-- <div class="upload">
      <div class="div-label">
        <label
          >请输入需要下载的文件<span style="font-weight: bold;padding-bottom:20px"
            ></span
          ></label
        >
        <el-input placeholder="请输入文件路径"></el-input>
      </div>
      <el-button
        @click="download"
        class="el-button-color add-button-box"
        size="medium"
        type="primary"
      >
        <i class="el-icon-download el-icon--right">下载文件</i>
      </el-button>
    </div> -->
  </div>
</template>

<script>
export default {
  name: "Transmit",
  data(){
    return{
      headers:{
         'Authorization': localStorage.getItem('token'),
      },
      uploadFles:[]
    }
  },
  methods:{
    loadFile(file,fileList){
        this.uploadFles=fileList
    },
    submit(){
      let file = this.uploadFiles[0]
      let reader = new FileReader()
      reader.readAsText(file.raw)
      reader.onloader=(e)=>{
        const fileString = e.target.result
        console.log(fileString);
      }
    }
  }
};
</script>

<style scoped>
.div-label{
    margin-top:100px;
}
.upload{
    width:500px;
    height:500px;
    margin-left:50px
}
</style>
