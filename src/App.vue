<template>
    <div id="app">
        <h1>WangEditor 演示</h1>
        <div
            style="width: 80%; margin: 0 auto; display: flex; flex-direction: row; text-align: left;"
        >
            <wang-editor-vue
                class="editor"
                v-model="content"
                style="flex: 1;"
                :config="config"
            ></wang-editor-vue>
            <div v-html="content" style="flex: 1; margin-left: 20px;"></div>
        </div>
    </div>
</template>

<script>
    import WangEditorVue from '@/components/WangEditorVue';

    export default {
        name: 'App',
        components: { WangEditorVue },
        data() {
            return {
                content: '我是初始化的内容',
                config: {

                }
            };
        },
    };
</script>

<style lang="less">
    #app {
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;

        .editor {
            text-align: left;
            width: 800px;
            margin: 0 auto;
        }
    }
</style>
