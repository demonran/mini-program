<template>
  <div>
    <section>
      <input maxlength="10" :value="from" placeholder="请输入出发地" />
      <mp-button @click="chooseLocation('from')" type="primary" btnClass="mb15">获取位置</mp-button>
    </section>
    <section>
      <mp-input v-model="to" placeholder="请输入目的地"></mp-input>
      <mp-button @click="chooseLocation('to')" type="primary" btnClass="mb15">获取位置</mp-button>
    </section>

    <div>
      <div class="info">
        <div class="user-info">
          <img src="https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=1243490651,2641972602&fm=26&gp=0.jpg"/>
          <p><span>张二娃</span><span>¥5/人</span></p>
          <p><span>川A ***678 大众 白色</span><span>4.9 分</span></p>
        </div>
        <p><span>今天19:22出发</span><span>  可载4人</span></p>
        <p>目的地：<span>四川省成都市天府五街G5</span></p>
        <p style="overflow: hidden">
          <img src="https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=1243490651,2641972602&fm=26&gp=0.jpg">
          <img src="https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=1243490651,2641972602&fm=26&gp=0.jpg">
          <img src="https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=1243490651,2641972602&fm=26&gp=0.jpg">
          <button>立即占座</button>
        </p>
      </div>
    </div>
  </div>

</template>

<script>
  import {chooseLocation,getLocation} from '@/utils/wx'
  import mpInput from 'mpvue-weui/src/input';
  import mpButton from 'mpvue-weui/src/button';

  export default {
    name: "passenger",
    components: {
      mpInput,
      mpButton
    },


    data(){
        return {
          from: '',
          to:''
        }
    },

    mounted(){
      console.log("mounted..")
      this.getLocation()
    },

    methods: {
      async chooseLocation(type) {
        const { name } = await chooseLocation();
        console.log(name)
        console.log(type)
        this[type] = name
      },

      async getLocation(){
       const res = await getLocation();
       console.log(res);

      }

    }
  }
</script>

<style scoped>
  .get-loc{
    width: 20rpx;
  }
  .user-info{
    overflow: hidden;
  }
  .user-info img{
    width: 88rpx;
    height: 88rpx;
    border-radius: 50%;
    float: left;
  }
  .info img{
    width: 88rpx;
    height: 88rpx;
    border-radius: 50%;
    float: left;
  }
</style>
