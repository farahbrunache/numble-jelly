<template>
  <div id="app">
    <Navbar/>
    <router-view/>
  </div>
</template>

<script>
import Navbar from '@/components/Navbar'
export default {
  name: 'App',
  components: {
    Navbar
  },
  methods:{

  }
}
</script>

<style>
html,
body,
p,
ol,
ul,
li,
dl,
dt,
dd,
blockquote,
figure,
fieldset,
legend,
textarea,
pre,
iframe,
hr,
h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0;
  padding: 0;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: 100%;
  font-weight: normal;
}

button,
input,
select,
textarea {
  margin: 0;
}

html {
  box-sizing: border-box;
}

*,
*:before,
*:after {
  box-sizing: border-box;
}

img,
embed,
iframe,
object,
audio,
video {
  height: auto;
  max-width: 100%;
}

iframe {
  border: 0;
}

table {
  border-collapse: collapse;
  border-spacing: 0;
}

td,
th {
  padding: 0;
  text-align: left;
}

body {
  font-family: "Abel", sans-serif;
}
h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: "Major Mono Display", monospace;
}
h2 {
  color: #ff7657;
  font-size: 1.8em;
  font-weight: bold;
  text-align: center;
}
</style>
