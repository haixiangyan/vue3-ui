<template>
<div class="layout">
  <TopNav class="nav"></TopNav>

  <div class="content">
    <aside v-if="menuVisible">
      <h2>文档</h2>
      <ol>
        <li>
          <router-link to="/docs/intro">介绍</router-link>
        </li>
        <li>
          <router-link to="/docs/install">安装</router-link>
        </li>
        <li>
          <router-link to="/docs/get-started">开始使用</router-link>
        </li>
      </ol>
      <h2>组件列表</h2>
      <ol>
        <li>
          <router-link to="/docs/switch">Switch 组件</router-link>
        </li>
        <li>
          <router-link to="/docs/button">Button 组件</router-link>
        </li>
        <li>
          <router-link to="/docs/dialog">Dialog 组件</router-link>
        </li>
        <li>
          <router-link to="/docs/tabs">Tabs 组件</router-link>
        </li>
      </ol>
    </aside>
    <main>
      <router-view></router-view>
    </main>
  </div>
</div>
</template>

<script lang="ts">
import TopNav from '../components/TopNav.vue';
import {inject, Ref} from "vue";

export default {
  name: "Docs",
  components: {
    TopNav,
  },
  setup() {
    const menuVisible = inject<Ref<boolean>>("menuVisible")

    return { menuVisible }
  }
}
</script>

<style scoped lang="scss">
.layout {
  display: flex;
  flex-direction: column;
  height: 100vh;
  > .nav {
    flex-shrink: 0;
  }
  > .content {
    flex-grow: 1;
    padding-top: 60px;
    padding-left: 156px;
    @media (max-width: 500px) {
      padding-left: 0;
    }
  }
}
.content {
  display: flex;
  > aside {
    flex-shrink: 0;
  }
  > main {
    flex-grow: 1;
    padding: 16px;
  }
}
aside {
  background: lightblue;
  width: 150px;
  padding: 70px 0 16px;
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  > h2 {
    margin-bottom: 4px;
    padding: 0 16px;
  }
  > ol {
    > li {
      > a {
        padding: 4px 16px;
        display: block;
      }

      .router-link-active {
        background: white;
      }
    }
  }
}
main {
  overflow: auto;
}
</style>
