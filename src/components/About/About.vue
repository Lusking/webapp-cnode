<template lang="html">
  <transition name="showAbout">
    <div class="about">
      <i @click="showAbout" class="close"></i>
      <div class="about-content">
        <h1>关于</h1>
        <h2>Vue.js打造一个开源的CNode社区</h2>
        <p class="skill"><b>技术栈</b>：</p>
        <div>Vue2<br>Vuex(不同组件状态共享)<br>vue-router(路由)<br>axios(发起http请求)<br>SASS(SCSS)<br>Express(上线版本是Koa2)<br>Webpack<br>Moment.js(时间处理)<br>ES6<br>localStorage(HTML5)<br>Canvas(页面顶部小雪花)<br>CSS3</div>
        <p class="url"><b>源码地址</b>：<a @touchstart="isHover=true" @touchEnd="isHover=false" :class="{hover: isHover}" href="https://github.com/Lusking/vue-cnode" target="_blank">GitHub</a></p>
        
      </div>
      <div @click="showAbout" class="mask"></div>
    </div>
  </transition>

</template>

<script>
export default {
  name: 'about',
  data() {
    return {
      isHover: false
    }
  },
  computed: {
    isShowAbout() {
      return this.$store.state.isShowAbout;
    }
  },
  methods: {
    showAbout() {
      this.$store.commit('showAbout', false);
    }
  }

}
</script>

<style lang="scss" scoped>
  a {
    color: #3F51B5;
  }

  .about {
    display: flex;
    position: absolute;
    z-index: 2;
    top: 0;
    left: 0;
    line-height: 30px;
    bottom: 0;
    right: 0;
    width: 100%;
    height: 100%;
    justify-content: center;
    align-items: center;
    // background-color: rgba(0, 0, 0, .5);
    .close {
      position: absolute;
      z-index: 3;
      display: inline-block;
      width: 30px;
      height: 30px;
      background: url('./close.svg') no-repeat;
      background-size: contain;
      top: 11%;
      right: 12%;
    }
    @media screen and (min-width: 760px) {
      .close {
        right: 26%;
      }
    }
    .about-content {
      position: relative;
      z-index: 2;
      width: 80%;
      height: 80%;
      background-color: white;
      border-radius: 10px;
      padding: 30px 10px;
      box-shadow: 0 0 20px gray;
      overflow: auto;

      h1 {
        text-align: center;
        font-size: 1.2rem;
        color: #31c27c;
        transition: .3s ease-in-out;
      }
      h1:hover {
        transform: rotate(15deg);
        transition: .3s ease-in-out;
      }
      h2 {
        font-size: 1.1rem;
        text-align: center;
      }
      p {
        text-indent: 1em;
        word-break: break-all;
        margin-top: 6px;

        b {
          display: inline-block;
          transition: .3s ease-in-out;
        }
        b:hover {
          transform: rotate(-10deg);
          transition: .3s ease-in-out;
        }

      }
      p.copyright {
        text-indent: 0;
      }
      div {
        // letter-spacing: 1px;
        padding-left: 50px;
      }
      .help {
        padding: 0;
        width: 100%;
        img {
          width: 100%;
          height: auto;
        }
      }
    }
    @media screen and (min-width: 760px) {
      .about-content {
        width: 50%!important;
      }
    }
    .mask {
      position: absolute;
      z-index: 0;
      width: 100%;
      height: 100%;
      background: none;
    }
  }
  .showAbout-enter-active {
    transition: all .4s ease-in-out;
  }
  .showAbout-leave-active {
    transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
  }
  .showAbout-enter, .showAbout-leave-active {
    transform: rotateZ(180deg);
    opacity: 0;
  }
</style>
