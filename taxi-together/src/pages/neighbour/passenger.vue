<template>
  <div>
    <section>
      <mp-input maxlength="10" :value="from" placeholder="请输入出发地"></mp-input>
      <mp-button @click="getLocation('from')" type="primary" btnClass="mb15">获取位置</mp-button>
    </section>
    <section>
      <mp-input v-model="from" placeholder="请输入目的地"></mp-input>
      <mp-button @click="getLocation('to')" type="primary" btnClass="mb15">获取位置</mp-button>
    </section>
  </div>

</template>

<script>
  import wx from '@/utils/wx'
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

    methods: {
      async getLocation (type) {
        const { name } = await wx.chooseLocation();
        console.log(name)
        this[type] = name
      },

    }
  }
</script>

<style scoped>
  .get-loc{
    width: 20rpx;
  }
</style>
