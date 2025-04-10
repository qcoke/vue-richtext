<template>
    <div class="rich-editor">
        <Toolbar style="border-bottom: 1px solid #ccc" :editor="editor" :defaultConfig="toolbarConfig" :mode="mode" />
        <Editor style="height: 500px; overflow-y: hidden;" v-model="html" :defaultConfig="editorConfig" :mode="mode"
            @onCreated="onCreated" />
    </div>
</template>
<script>
import { Editor, Toolbar } from '@wangeditor/editor-for-vue'
import { Boot } from '@wangeditor/editor'
import formulaModule from '@wangeditor/plugin-formula'

Boot.registerModule(formulaModule)

export default {
    name: "TheRichEditor",
    components: { Editor, Toolbar },
    data() {
        return {
            editor: null,
            html: '<p>hello</p>',
            toolbarConfig: {
                insertKeys: {
                    index: 0,
                    keys: [
                    'insertFormula', // “插入公式”菜单
                    // 'editFormula' // “编辑公式”菜单
                    ],
                },
            },
            editorConfig: {
                placeholder: '请输入内容...',
                hoverbarKeys: {
                    formula: {
                        menuKeys: ['editFormula'], // “编辑公式”菜单
                    },
                },
            },
            mode: 'default', // or 'simple'
        }
    },
    mounted() {
        // 模拟 ajax 请求，异步渲染编辑器
        setTimeout(() => {
            this.html = '<p>模拟 Ajax 异步设置内容 HTML</p>'
        }, 1500)
    },
    beforeDestroy() {
        const editor = this.editor
        if (editor == null) return
        editor.destroy() // 组件销毁时，及时销毁编辑器
    },
    methods: {
        onCreated(editor) {
            this.editor = Object.seal(editor) // 一定要用 Object.seal() ，否则会报错
        },
    }
}
</script>
<style src="@wangeditor/editor/dist/css/style.css"></style>