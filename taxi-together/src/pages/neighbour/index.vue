<template>
  <div>
    <mp-navbar :tabs="tabs" :active-index="activeIndex" @tabClick="tabClick"></mp-navbar>
    <passenger v-if="activeIndex==0"></passenger>
    <driver v-if="activeIndex==1"></driver>
  </div>
</template>

<script>
  import mpNavbar from 'mpvue-weui/src/navbar';
  import driver from './driver';
  import passenger from './passenger';

  export default {
    data() {
      return {
        activeIndex: 0,
        tabs: ['乘客', '司机']
      }
    },

    components: {
      mpNavbar,
      driver,
      passenger
    },

    methods: {
      tabClick(index) {
        this.activeIndex = index
      },
      clickHandle(ev) {
        console.log('clickHandle:', ev)
        // throw {message: 'custom test'}
      }
    },

    created() {
      // let app = getApp()
    }
  }
</script>

<style scoped>
  .userinfo {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .userinfo-avatar {
    width: 128 rpx;
    height: 128 rpx;
    margin: 20 rpx;
    border-radius: 50%;
  }

  .userinfo-nickname {
    color: #aaa;
  }

  .usermotto {
    margin-top: 150px;
  }

  .form-control {
    display: block;
    padding: 0 12px;
    margin-bottom: 5px;
    border: 1px solid #ccc;
  }

  .all {
    width: 7.5rem;
    height: 1rem;
    background-color: blue;
  }

  .all:after {
    display: block;
    content: '';
    clear: both;
  }

  .left {
    float: left;
    width: 3rem;
    height: 1rem;
    background-color: red;
  }

  .right {
    float: left;
    width: 4.5rem;
    height: 1rem;
    background-color: green;
  }
</style>
