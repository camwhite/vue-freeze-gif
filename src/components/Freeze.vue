<template>
  <figure v-freeze="source"></figure>
</template>
<script>
export default {
  name: 'freeze',
  props: [ 'source' ],
  directives: {
    freeze: {
      inserted (el, { value }, vnode) {
        const source = value
        const { offsetWidth, offsetHeight } = vnode.elm
        const image = document.createElement('img')
        image.src = source

        const isGif = source.split('.').pop() === 'gif'
        if (!isGif) {
          el.appendChild(image)
          return
        }
        el.innerHTML = '<p class="gif">GIF</p>'

        const poster = document.createElement('canvas')
        poster.width = offsetWidth
        poster.height = offsetHeight
        el.appendChild(poster)

        image.addEventListener('load', (evt) => {
          poster.getContext('2d').drawImage(image, 0, 0, offsetWidth, offsetHeight)
        })
        let playing = false
        el.addEventListener('mouseenter', (evt) => {
          if (playing) return
          el.replaceChild(image, poster)
          playing = true
        })
        el.addEventListener('mouseleave', (evt) => {
          if (!playing) return
          el.replaceChild(poster, image)
          playing = false
        })
      }
    }
  }
}
</script>
<styte lang="stylus" scoped>
.gif
  position absolute !important
  top 5px
  left 5px
  padding 0.2 rem
  font-size 18px
  font-family 'Helvetica', sans-serif
  background rgba(black, 0.4)
  color white
  border-radius 4px
figure
  position relative
  width 100%
  height 100%
img
  width 100%
  height 100%
  object-fit cover
</styte>
