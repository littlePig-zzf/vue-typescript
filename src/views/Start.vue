<template>
  <div class="start">
    <div class="item">
      <label class="title">打字机效果</label>
      <div ref="typeWriteTxt">
        暂时想不出什么有趣的动画......

        前段时间吧，每到了下午的时候，就是会觉得特别难熬咯，然后各种烦躁，想着辞职啊，做什么岗位啊，等等。
        之前想做什么运营呢还是产品呢，我现在通通不想做了。

        现在我倒觉得有一份轻松的工作，下班业余时间比较多，可以学点其他东西，但是可能就是没有实践只停留在学，也就是只有输入没有输出

        如何更好地输入知识呢？

        学习那么多知识，倒不如把一个知识点用得特别溜
      </div>
    </div>

    <div class="item">
      <label class="title">加载中动画/播放器</label>
      <div class="spinner">
        <div class="h1 spinner-item"></div>
        <div class="h2 spinner-item"></div>
        <div class="o">
          <svg viewBox="0 0 24 12">
            <path class="loading_o-path" d="M7.4,12c0-3.8,2.5-5.6,5.1-5.6s5.1,1.8,5.1,5.6h6.9a11.67,11.67,0,0,0-12-12A11.73,11.73,0,0,0,.5,12H7.4Z" transform="translate(-0.5 0)"></path>
          </svg>
        </div>
        <div class="w1 spinner-item"></div>
        <div class="w2 spinner-item"></div>
        <div class="w3 spinner-item"></div>
        <div class="l1 spinner-item"></div>
        <div class="t1 spinner-item"></div>
        <div class="t2"></div>
      </div>
    </div>

    <div class="item">
      <label class="title">时钟</label>
      <span class="clock"></span>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
@Component({
  components: {}
})
export default class Start extends Vue {
  typeWriteText: string = "";
  timer: any = "";

  mounted() {
    let el: any = this.$refs.typeWriteTxt;
    this.typeWriteText = el.innerText;
    el.innerText = "";

    this.startHandle();
  }

  startHandle() {
    let index = 0;
    let resEl: any = this.$refs.typeWriteTxt;
    const str = this.typeWriteText;
    this.timer = setInterval(() => {
      if (index > str.length) {
        clearInterval(this.timer);
      }
      resEl.innerText = str.substring(0, index++);
    }, 200);
  }
}
</script>
<style scoped lang="scss">
.start {
  text-align: left;
  .item {
    margin-bottom: 30px;
    .spinner {
      .spinner-item {
        width: 4px;
        height: 7px;
        display: inline-block;
        margin-right: 5px;
        background: #42b983;
        transform-origin: center bottom;
        animation: scaleAni 0.5s infinite ease-in-out;
        &:first-child {
          margin-right: 8px;
        }
      }
      .o {
        width: 14px;
        height: 7px;
        margin-right: 5px;
        display: inline-block;
        overflow: hidden;
        svg {
          vertical-align: top;
          .loading_o-path {
            fill: #42b983;
          }
        }
      }
      .t1 {
        margin-left: 2px;
        animation-delay: -0.6s;
      }
      .t2 {
        width: 11px;
        height: 3px;
        margin-left: -12px;
        display: inline-block;
        background: #42b983;
        animation-delay: -0.5s;
      }
      .w1 {
        animation-delay: -1s;
      }
      .w2 {
        animation-delay: -0.9s;
      }
      .w3 {
        animation-delay: -0.8s;
      }
      .l1 {
        animation-delay: -0.7s;
      }
    }
  }
  .title {
    display: inline-block;
    margin-bottom: 10px;
    font-size: 14px;
    font-weight: 700;
  }
  .clock {
    position: relative;
    width: 60px;
    height: 60px;
    display: block;
    border: 6px solid rgb(245, 122, 122);
    border-radius: 50%;
    animation: rotateAni 1s linear infinite;
    &::before {
      position: absolute;
      display: inline-block;
      left: 50%;
      top: 50%;
      margin-top: -2px;
      content: "";
      width: 14px;
      height: 6px;
      border-radius: 5px;
      background: rgb(245, 122, 122);
      transform-origin: left center;
    }
  }
}

@keyframes scaleAni {
  0%,
  40%,
  100% {
    transform: scaleY(1);
  }
  20% {
    transform: scaleY(1.4);
  }
}

@keyframes rotateAni {
  0% {
    transform: rotate(0);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
