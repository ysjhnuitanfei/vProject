<template>
  <div class='testSwiper' id='testSwiper'>
    <div @click="previewImg">
      <swiper ref="mySwiper" :options="options">
        <swiper-slide v-for="(item,index) in imgList" :key="index">
          <img class="full " :src="item" alt=" ">
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
    <previewer :list="list" ref="previewer" :options="previewOptions" @on-close=""></previewer>
  </div>
</template>
<script>
// import API from '@/api'
// import Utils from '@/utils'
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
import { Previewer, TransferDom } from 'vux'
export default {
  name: 'testSwiper',
  components: {
    swiper,
    swiperSlide,
    Previewer
  },
  directives: {
    TransferDom
  },
  computed: {
    swiper () {
      return this.$refs.mySwiper.swiper
    },
    list () {
      if (this.imgList && this.imgList.length > 0) {
        return this.imgList.map(item => ({
          src: item,
          w: document.documentElement.clientWidth,
          h: 600
        }))
      }
    }
  },
  data () {
    return {
      previewOptions: {
        loop: false,
        fullscreenEl: false,
        captionEl: true,
        closeEl: false,
        counterEl: false,
        addCaptionHTMLFn: function (item, captionEl, isFake) {
          // item      - slide object
          // captionEl - caption DOM element
          // isFake    - true when content is added to fake caption container
          //             (used to get size of next or previous caption)

          captionEl.children[0].innerHTML = 'asdasdasdasdasdasdasd'
          return true
        },
        shareButtons: [
          {id: 'wechat', label: '分享微信', url: '#'},
          {id: 'weibo', label: '新浪微博', url: '#'},
          {id: 'download', label: '保存图片', url: '{{raw_image_url}}', download: true}
        ],
        parseShareButtonOut: function (shareButtonData, shareButtonOut) {
          // `shareButtonData` - object from shareButtons array
          // `shareButtonOut` - raw string of share link element
          return shareButtonOut
        }
      },
      imgList: [
        'https://memberwsdl.vivo.com.cn/member/icon/2018/03/2018032317122789692742.jpg',
        'https://memberwsdl.vivo.com.cn/member/icon/2018/03/2018032316425452759503.jpg',
        'https://memberwsdl.vivo.com.cn/member/icon/2018/01/2018012410091332376522.jpg',
        'https://memberwsdl.vivo.com.cn/member/static/img/level-1.c7b5d67.png.webp'
      ],
      options: {
        effect: 'coverflow',
        grabCursor: true,
        centeredSlides: true,
        slidesPerView: 'auto',
        loop: true,
        coverflowEffect: {
          rotate: 0,
          stretch: 50,
          depth: 100,
          modifier: 1,
          slideShadows: false
        },
        pagination: {
          el: '.swiper-pagination'
        }
      }
    }
  },

  methods: {
    close () {
      this.$refs.previewer.close()
    },
    previewImg () {
      var currentIndex = this.swiper.activeIndex % this.imgList.length
      this.$refs.previewer.show(currentIndex)
    }
  }
  // async mounted() {
  // API访问
  // let response = await API.testSwiper.getInfo({});
  // let result = response.data;
  // this.$nextTick(() => { })
  // }
}
</script>
<style lang="less">
.testSwiper {
  .swiper-slide {
    width: 700px;
    height: 600px;
  }

  .pswp__ui {
    .pswp__caption--empty {
      display: block;
    }
    .pswp__caption__center {
      font-size: 50px;
      padding: 0;
      max-width: 100%;
    }
  }
}
</style>
