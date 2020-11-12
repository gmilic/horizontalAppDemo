<template>
  <div class="wrapper">
    <div class="sliding-bg" ref="slidingBg" :style="{ backgroundPositionX: `${bgPosition}` }">
      <div ref="draggableContainer" id="draggable-container" @mousedown="dragMouseDown">
        <img name="header" src="../assets/telefon.png" alt="phone" />
        <h4 v-if="showDragMe">Drag me!</h4>
        <div v-if="showChair" class="showChairWrapp">Chair</div>
      </div>
    </div>
    {{ positions.clientX }}
    {{ bgPosition }}

  </div>
</template>

<script>
export default {
  name: 'AppDemo2',
  data: function () {
    return {
      positions: {
        clientX: undefined,
        // clientY: undefined,
        movementX: 0,
        // movementY: 0
      },
      bgPosition: 0,
      showDragMe: true,
      showChair: false
    }
  },
  methods: {
    dragMouseDown: function (event) {
      event.preventDefault()
      this.showDragMe = false;
      // get the bg position at startup:
      this.positions.clientX = this.$refs.slidingBg.style.backgroundPositionX

      document.onmousemove = this.elementDrag
      document.onmouseup = this.closeDragElement
    },
    elementDrag: function (event) {
      event.preventDefault()
      // calculate new bg position
      this.positions.movementX = this.positions.clientX - event.movementX

      this.positions.clientX = parseInt(this.$refs.slidingBg.style.backgroundPositionX)
      

      // set the bg new position:
      this.bgPosition = this.positions.movementX + 'px'
    },
    closeDragElement () {
      document.onmouseup = null;
      document.onmousemove = null;
      this.showDragMe = true;
      this.showChair = false;
    }
  },
  computed: {
    // showChairCalc: function() {
    //   if (this.positions.clientX > 970 ) {
    //     return this.showChair = true
    //   } else {
    //     return this.showChair = false
    //   }
    // }
  }
}
</script>

<style scoped>
  .wrapper {
    overflow: hidden;
    position: relative;
  }
  .sliding-bg {
    background: url('../assets/bg.jpg') repeat-x 0 center;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
    height: 50vh;
    width: 100vw;
    animation: slide 60s linear infinite;

  }
  #draggable-container {
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
  }
  h4 {
    color: #eee;
    text-shadow: 2px 2px 6px #000;
    font-size: 2em;
    position: absolute;
    top: 39%;
    left: 16%;
    font-family: sans-serif;
  }
  .showChairWrapp {
    color: #eee;
    text-shadow: 2px 2px 6px #000;
    font-size: 2em;
    position: absolute;
    top: 39%;
    left: 16%;
    font-family: sans-serif;
  }
</style>