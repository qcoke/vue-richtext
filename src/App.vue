<template>
  <div id="app">
    <el-container>
      <el-header class="main-header">Header</el-header>
      <el-container>
        <el-aside class="main-left">Aside</el-aside>
        <el-main class="main-container">
          <div id="rich-editor">
            <TheRichEditor />
          </div>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import TheRichEditor from './components/TheRichEditor.vue';

export default {
  name: 'App',
  components: {
    TheRichEditor
  },
  methods: {
    showSuccess() {
      this.$message({
        message: 'Hello World',
        type: 'success'
      });
    }
  }
}
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
  min-height: 100vh;
  overflow-x: hidden;
  margin: 0;
  padding: 0;
}
</style>
<style scoped>
:deep(.el-container) {
  height: 100vh;
}

.main-header {
  background-color: rgb(203, 203, 203, 0.5);
}

.main-left {
  width: 200px;
  background-color: rgba(144, 143, 143, 0.5);
}
#rich-editor {
  width: 800px;
  min-height: 500px;
  border: 1px solid #ccc;
  box-sizing: border-box;
}
</style>
