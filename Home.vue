<template>
  <transition name="abc">
    <section>
      <h2>这是home页面</h2>
      <div class="swiper-container">
        <div class="swiper-wrapper">
          <div class="swiper-slide" v-for="item in dataSource">
            <img :src="item" alt="">
          </div>
        </div>
        <!-- 如果需要分页器 -->
        <div class="swiper-pagination"></div>

        <!-- 如果需要导航按钮 -->
        <div class="swiper-button-prev"></div>
        <div class="swiper-button-next"></div>
      </div>
    </section>
  </transition>

</template>

<script>
    import * as Swiper from 'swiper';
    // import * as $ from 'jquery';
    export default {
        name: "Home",
        //生命周期函数, 当组件创建完毕之后触发, 在该函数里无法获取组件里的标签
        created(){
          // console.log('created---', $('h2'));
        },
        //生命周期函数, 当组件创建完毕且挂载完毕之后触发, 在该函数里可以获取组件里的标签
        mounted(){
          // console.log('mounted---', $('h2'));
          // console.log(Swiper);
          new Swiper["default"]('.swiper-container', {
            direction: 'horizontal', // 水平切换选项
            loop: true, // 循环模式选项

            // 如果需要分页器
            pagination: {
              el: '.swiper-pagination',
            },

            // 如果需要前进后退按钮
            navigation: {
              nextEl: '.swiper-button-next',
              prevEl: '.swiper-button-prev',
            }
          });
        },
      data(){
          return {
            dataSource:[
              "http://www.placehold.it/600x301",
              "http://www.placehold.it/600x302",
              "http://www.placehold.it/600x303",
              "http://www.placehold.it/600x304",
              "http://www.placehold.it/600x305"
            ]
          }
      }
    }
</script>

<style scoped>
  @import "../../node_modules/swiper/dist/css/swiper.min.css";
  section {
    margin-top: 150px;
  }
  .swiper-container {
     width: 600px;
     height: 300px;
     margin: 0 auto;
   }
  .abc-enter, .abc-leave-to {
    opacity: 0;
    transform: rotate(360deg);
  }
  .abc-enter-active, .abc-leave-active {
    transition: 1s ease;
  }
</style>
