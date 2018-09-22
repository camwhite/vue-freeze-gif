# Vue Freeze Gif

*Vue component to play / pause gifs*

![demo](https://media.giphy.com/media/7OX3GLk3KAtZ0BPqif/giphy.gif)

### Installation

`npm i -S vue-freeze-gif`

### Setup

```js
import Vue from 'vue'
import VueFreezeGif from 'vue-freeze-gif'
import 'vue-freeze-gif/lib/vue-freeze-gif.css'

Vue.component('freeze', VueFreezeGif)

...

```

### Usage

Once declared the freeze component takes a `source` prop refering to `<img src="some.gif" />`

```js
<template>
  <freeze source="https://giphy.com/some.gif" />
</template>
```

The component is able to handle images of any MIME type in the case of dynamic rendering.
It will also take on the dimensions of it's parent.

```js
<template>
  <ul>
    <li v-for="image of images">
      <freeze :source="image.src" />
    </li>
  </ul>
</template>
<style>
li {
  width: 256px;
  height: 256px;
}
</style>
```

### Contributing

clone and install

`git clone https://github.com/camwhite/vue-freeze-gif.git && cd $_ && yarn install`

edit the source component

`vi src/components/Freeze.vue`

running the dev server to try it out

`yarn run serve`

building the library

`yarn run build:bundle`
