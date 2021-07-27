<template>
    <div class="wang-editor-vue" id="wangEditor"></div>
</template>

<script>
    import E from 'wangeditor';

    export default {
        name: 'WangEditorVue',
        data() {
            return {
                editor: undefined,
                defaultConfig: {
                    onchangeTimeout: 100,
                    withCredentials: true,
                    uploadImgShowBase64: true,
                    excludeMenus: ['emoticon', 'video', 'quote'],
                },
            };
        },
        mounted() {
            this.init();
        },
        props: {
            value: String,
            config: {
                type: Object,
            },
        },
        methods: {
            init() {
                this.editor = new E('#wangEditor');
                this.editor.config.onchange = html => {
                    this.$emit('input', html);
                };

                let config = Object.assign({}, this.defaultConfig, this.config);
                Object.keys(config).forEach(key => {
                    this.editor.config[key] = config[key];
                });

                this.editor.create();
                if (this.value) {
                    this.editor.txt.html(this.value);
                }
            },
        },
    };
</script>

<style scoped>
    .wang-editor-vue {
    }
</style>
