<template>
	<div class="banner">
		<swiper :options="swiperOption" ref="mySwiper">
      <!-- 务必加上key 2.0后-->
       <swiper-slide v-for="(item,index) in listImg" :key="index">
         <img :src="item.url">
       </swiper-slide>
       <div class="swiper-pagination" slot="pagination"></div>
     </swiper>
	</div>
</template>
<script>
import { swiper, swiperSlide } from 'vue-awesome-swiper'
require('swiper/dist/css/swiper.css')
	export default{
		props: ['listImg'],
		data(){
			return{
				swiperOption: {
        notNextTick: true,
        autoplay: 3000,
        pagination: '.swiper-pagination',
        paginationClickable: true,
        mousewheelControl: true,
        autoplayDisableOnInteraction: false,//移动端加上这个不然不会滚动
        loop: true,//环路
        observeParents: true,
        onSlideChangeEnd: swiper => {
          this.page = swiper.realIndex + 1
          this.index = swiper.realIndex
        }
      }
			}
		},
		components:{
			swiper,
    	swiperSlide
		},
		computed: {
      swiper() {
        return this.$refs.mySwiper.swiper
      }
    },
		mounted(){
      this.swiper.slideTo(0, 0, false)     
		}
	}
</script>
<style>
.banner{
  margin-top: 60px;
}
  .swiper-slide img {
    width: 100%;
    height: 100%;
  }
</style>