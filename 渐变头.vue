<template>
  <div class='demo1' id='demo1'>
    <div class="header" :class="['back',showBg?'header-bg':'']">
      <span @click="back"></span>
      <div class="content">内容</div>
    </div>
    <div class="header-white">
      <span @click="back"></span>
    </div>
    <div class="page-content">
      sadasdasdasd
    </div>
  </div>
</template>
<script>
  // import API from '@/api'
  // import Utils from '@/utils'
  export default {
    name: 'demo1',
    components: {},
    data () {
      return {
        showBg: false
      }
    },
    created () {
      console.log(location.href)
      window.vivojsbridge.call('showTitle', {
        show: false
      })
      window.addEventListener('scroll', this.scrollPage)
    },
    methods: {
      back () {
        location.href = location.href + '?immer=1'
        // window.history.go(-1)
        // if (window.history.length == 1) {
        //   location.href = 'vivogame://game.vivo.com/openjump?j_type=104&tab=0'
        // }
      },
      scrollPage () {
        console.log(window.scrollY)
        var distanceSroll = 400
        if (window.scrollY > distanceSroll) {
          document.querySelector('.header').style = 'opacity:1'
        } else {
          // document.querySelector('.header').style = 'opacity:0'
          document.querySelector('.header').style = 'opacity:' + (window.scrollY - 10) / (distanceSroll - 10)
        }
      }
    }
    // async mounted() {
    // API访问
    // let response = await API.demo1.getInfo({});
    // let result = response.data;
    // this.$nextTick(() => { })
    // }
  }
</script>
<style lang="less">
// .demo1  {
//   color: red;
// }
.demo1 {
  background: green;
  height: 4080px;
  .page-content {
    padding-top: 500px;
  }
  .header {
    position: fixed;
    top: 0;
    height: 1.8rem;
    width: 100%;
    color: black;
    background-color: white;
    opacity: 0;
    z-index: 1;
    span {
      float: left;
      width: 144px;
      height: 180px;
      background-color: inherit;
      z-index: 999;
    }
    .content {
      margin-top: 85px;
      top: 40px;
    }
  }
  .header-white {
    position: fixed;
    height: 1.8rem;
    width: 100%;
  }

  .header-white span:after {
    width: 0.3rem;
    height: 0.3rem;
    border: 0.03rem solid white;
    position: absolute;
    top: 1.3rem;
    left: 0.7rem;
    border-width: 0.04rem 0.04rem 0 0;
    content: '';
    transform: rotate(-135deg) translateY(-50%);
    transform-origin: 50% 0;
  }
  .header span:after {
    width: 0.3rem;
    height: 0.3rem;
    border: 0.03rem solid #000;
    position: absolute;
    top: 1.3rem;
    left: 0.7rem;
    border-width: 0.04rem 0.04rem 0 0;
    content: '';
    transform: rotate(-135deg) translateY(-50%);
    transform-origin: 50% 0;
  }
}
</style>
