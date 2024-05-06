<template>
    <div class="layout">
        <Topnav :toggleMenuButtonVisible="true" class="nav" />
        <div class="content">
            <aside v-if="visible">
                <h2>文档</h2>
                <ol>
                    <li>
                        <router-link to="/doc/intro">介绍</router-link>
                    </li>
                    <li>
                        <router-link to="/doc/install">安装</router-link>
                    </li>
                    <li>
                        <router-link to="/doc/get-started">开始使用</router-link>
                    </li>
                </ol>
                <h2>组件列表</h2>
                <ol>
                    <li>
                        <router-link to="/doc/switch">Switch 组件</router-link>
                    </li>
                    <li>
                        <router-link to="/doc/button">Button 组件</router-link>
                    </li>
                    <li>
                        <router-link to="/doc/dialog">Dialog 组件</router-link>
                    </li>
                    <li>
                        <router-link to="/doc/tabs">Tabs 组件</router-link>
                    </li>
                </ol>
            </aside>
            <main>
                <router-view />
            </main>
        </div>
    </div>
</template>

<script lang="ts">
import Topnav from "../components/Topnav.vue";
import { inject, Ref } from 'vue';
export default {
    components: { Topnav },
    setup() {
        const visible = inject<Ref<boolean>>('menuvisible') // get
        // console.log('Doc aside 获取的 menuvisible 为:' + visible.value)
        return { visible }
    }
}
</script>





<style lang="scss" scoped>
.router-link-active{
    text-decoration: underline;
    background-color: white;
}
.layout {
    display: flex;
    flex-direction: column;
    height: 100vh;
    z-index: 5;

    >.nav {
        flex-shrink: 0;
    }

    >.content {
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

    >aside {
        flex-shrink: 0;
    }

    >main {
        flex-grow: 1;
        padding: 16px;
        background: white;
    }
}

aside {
    background-color: lightblue;
    width: 150px;
    padding: 16px;
    position: fixed;
    top: 0;
    left: 0;
    padding-top: 70px;
    height: 100%;
    display: block;
    z-index: 1;

    >h2 {
        margin-bottom: 4px;
    }

    >ol {
        >li {
            padding: 4px 0;
        }
    }

    @media (max-width: 500px) {
        position: fixed;
        top: 0;
        left: 0;
        padding-top: 70px;
    }
}

main {
    overflow: auto;
}
</style>