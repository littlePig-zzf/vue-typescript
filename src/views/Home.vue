<template>
  <div class="home">
    <HelloWorld msg="欢迎来到zzf的工厂！这里充满着各种神奇的事情，一起来看看嘛？" @btnHandle="btnHandle"/>
    <span class="poster">
      <img src="../assets/dl.jpg" alt="">
    </span>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

@Component({
  components: {
    HelloWorld
  }
})
export default class Home extends Vue {
  // data
  //   @Provide()
  isCollapsed: boolean = false;

  //computed
  get rotateIcon() {
    return ["menu-icon", this.isCollapsed ? "rotate-icon" : ""];
  }
  get menuitemClasses(): Array<string> {
    return ["menu-item", this.isCollapsed ? "collapsed-menu" : ""];
  }

  // methods
  collapsedSider() {
    let el: any = this.$refs.side1;
    el.toggleCollapse();
  }

  btnHandle() {}
}
</script>
<style scoped lang="scss">
.layout {
  background: #f5f7f9;
  position: relative;
  border-radius: 4px;
  overflow: hidden;
}
.layout-header-bar {
  background: #fff;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.1);
}
.layout-logo-left {
  width: 90%;
  height: 30px;
  background: #5b6270;
  border-radius: 3px;
  margin: 15px auto;
}
.menu-icon {
  transition: all 0.3s;
}
.rotate-icon {
  transform: rotate(-90deg);
}
.menu-item span {
  display: inline-block;
  overflow: hidden;
  width: 69px;
  text-overflow: ellipsis;
  white-space: nowrap;
  vertical-align: bottom;
  transition: width 0.2s ease 0.2s;
}
.menu-item i {
  transform: translateX(0px);
  transition: font-size 0.2s ease, transform 0.2s ease;
  vertical-align: middle;
  font-size: 16px;
}
.collapsed-menu span {
  width: 0px;
  transition: width 0.2s ease;
}
.collapsed-menu i {
  transform: translateX(5px);
  transition: font-size 0.2s ease 0.2s, transform 0.2s ease 0.2s;
  vertical-align: middle;
  font-size: 22px;
}

.home {
  .poster {
    position: relative;
    display: inline-block;
    margin: 20px;
    font-size: 0;
    overflow: hidden;
    img {
      border-radius: 10px;
      z-index: 0;
    }
    &:hover {
      &::before {
        transform: rotate(90deg) translateX(320px);
        transform-origin: 0 100%;
      }
    }
    &::before {
      content: "";
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background: rgba(172, 252, 255, 0.2);
      border-radius: 10px;
      z-index: 1;
      transition: all 0.2s linear;
    }
  }
}
</style>
