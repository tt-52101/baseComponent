<!-- 自定义配置 -->
<template>
  <div>
    <el-form-item label="设置路径">
      <avue-switch v-model="main.activeOption.setUp"></avue-switch>
    </el-form-item>

    <el-form-item label="路径坐标">
      <el-input type="textarea" :rows="5"  v-model="main.activeOption.points"></el-input>
    </el-form-item>

    <el-form-item label="线条颜色">
      <avue-input-color color-format="hex" :show-alpha="false" placeholder="请选择颜色" v-model="main.activeOption.color" ></avue-input-color>
    </el-form-item>

    <el-form-item label="线条宽度">
      <avue-input-number v-model="main.activeOption.width"></avue-input-number>
    </el-form-item>

    <el-form-item label="虚线长度">
      <avue-input-number v-model="main.activeOption.dasharray"></avue-input-number>
    </el-form-item>
    <el-form-item label="透明度">
      <avue-input-number maxRows="1" minRows="0" precision="1"  v-model="main.activeOption.opacity"></avue-input-number>
    </el-form-item>

    <el-form-item label="动画速度">
      <avue-input-number  v-model="main.activeOption.speed"></avue-input-number>
    </el-form-item>

    <el-form-item label="显示条件">
      <avue-input v-model="main.activeOption.addr" style="width: 120px"></avue-input>
      =
      <avue-input v-model="main.activeOption.openVal" style="width: 70px"></avue-input>
    </el-form-item>

  </div>
</template>

<script>
export default {
  inject: ["main"],
  data() {
    return {
      show: false,
      textarea: ''
    }
  },
  computed(){
    //this.init()
  },
  mounted() {
    window.addEventListener('keyup', this.handleKeyup)

  },
  methods: {
    init(){
      if (this.main.activeOption.speed === undefined){
        this.main.activeOption.speed = 3
      }
      if (this.main.activeOption.opacity === undefined){
        this.main.activeOption.opacity = 1
      }
      if (this.main.activeOption.dasharray === undefined){
        this.main.activeOption.dasharray = 10
      }
      if (this.main.activeOption.width === undefined){
        this.main.activeOption.width = 10
      }
      if (this.main.activeOption.color === undefined){
        this.main.activeOption.color = "#FFFFFF"
      }
      //console.log(this.main.activeOption.speed)
    },


    handleKeyup(e) {
      if (e.key === 'q') {
        let x = Number(this.main.activeObj.left + 40).toFixed(0)
        let y = Number(this.main.activeObj.top + 40).toFixed(0)
        if (this.main.activeOption.points === undefined){
          this.main.activeOption.points = x + "," + y + " "
        }else {
          this.main.activeOption.points = this.main.activeOption.points + x + "," + y + " "
        }
      }

    },
    touchmove(e) {
      //console.log(e)
    }
  }
}
</script>

<style>
</style>
