<template>
  <div id="chaoModal" v-if="isModal">
    <div class="mask"></div>
    <div class="modal">
      <div class="info">
        <div class="infoInner">{{modalInfo}}</div>
      </div>
      <div class="confirmBtn" @click="confirm">好的</div>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    isModal:Boolean,
    modalInfo:String
  },
  data(){
    return {
      isModalCopy:this.isModal,
      modalInfoCopy:this.modalInfo
    }
  },
  methods:{
    confirm(){
      this.isModalCopy = false
      this.modalInfoCopy = "..."
      this.$emit('update:isModal',false)
      this.$emit('update:modalInfo',"...")
    }
  },
}
</script>

<style lang="less" scoped>
#chaoModal{
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  .mask{
    height: 100%;
    width: 100%;
    opacity: .2;
    background-color: #ccc;
  }
  .modal{
    position: absolute;
    left: 50%;
    top: 50%;
    margin-top: -140px;
    margin-left: -270px;
    width:540px;
    height:280px;
    background:rgba(255,255,255,1);
    border-radius:28px;
    .info{
      display: flex;
      align-items: center;
      padding: 0 75px 0 75px;
      height: 192px;
      border-bottom: 0.5px solid #BEBEC0;
      color:#000;
      font-size: 26px;
      .infoInner{
        width: 100%;
        text-align: center;
      }
    }
    .confirmBtn{
      line-height: 88px;
      text-align: center;
      color:#333;
      font-size: 34px;
      font-weight:600;
      cursor: pointer;
    }
  }
}
</style>