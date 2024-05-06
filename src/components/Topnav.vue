<template>
  <div class="topnav">
    <router-link to="/" class="logo">
      <svg class="icon">
        <use xlink:href="#icon-shouye"></use>
      </svg>
    </router-link>
    <ul class="menu">
      <li>
        <router-link to="/doc">文档</router-link>
      </li>
    </ul>
    <svg v-if="toggleMenuButtonVisible" class="toggleAside" @click="toggleMenu">
      <use xlink:href="#icon-menu"></use>
    </svg>
  </div>
</template>

<script lang="ts">
import { inject, Ref } from "vue";
export default {
  props: {
    toggleMenuButtonVisible: {
      tpye: Boolean,
      default: false
    }
  },
  setup() {
    const visible = inject<Ref<boolean>>("menuvisible");         // get
    // console.log('topnav 获取的 menuvisible 为：'+ visible.value)
    const toggleMenu = () => {
      visible.value = !visible.value;
    }
    return { toggleMenu };
  }
}
</script>

<style lang="scss" scoped>
$color: #128d87;

.topnav {
  $color: $color;
  display: flex;
  padding: 16px;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 10;
  justify-content: center;
  align-items: center;

  >.logo {
    max-width: 1.5em;
    margin-right: auto;

    >svg {
      width: 40px;
      height: 32px;
    }
  }

  >.menu {
    display: flex;
    white-space: nowrap;
    flex-wrap: nowrap;

    >li {
      margin: 0 1em;
    }
  }

  >.toggleAside {
    width: 32px;
    height: 32px;
    position: absolute;
    left: 0px;
    top: 50%;
    transform: translateY(-50%);
    display: none;
  }

  @media(max-width:500px) {
    >.menu {
      display: none;
    }

    >.logo {
      margin: 0 auto;
      display: inline-block;
      margin-right: 0px;
    }

    >.toggleAside {
      display: inline-block;
    }
  }
}
</style>