<template>
  <div id="app">
    <FormatText />
  </div>
</template>

<script>
import FormatText from './components/FormatText.vue'

export default {
  name: 'App',
  components: {
    FormatText
  }
}
</script>

<style>
/* Global Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 16px;
  scroll-behavior: smooth;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
  line-height: 1.6;
  color: #1e293b;
  background: #f8fafc;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#app {
  min-height: 100vh;
}

/* Scrollbar Styling */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: #f1f5f9;
}

::-webkit-scrollbar-thumb {
  background: #cbd5e1;
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: #94a3b8;
}

/* Selection Styling */
::selection {
  background: rgba(102, 126, 234, 0.2);
  color: inherit;
}

/* Focus Outline Reset */
*:focus {
  outline: none;
}

/* Print Styles */
@media print {
  body {
    background: white !important;
  }
}
</style>
