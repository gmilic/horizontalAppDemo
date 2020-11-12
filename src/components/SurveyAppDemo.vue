<template>
  <div class="wrapper">
    <div class="sliding-bg">
      <div ref="draggableContainer" id="draggable-container" @mousedown="dragMouseDown">
        <img name="header" src="../assets/telefon.png" alt="phone" />
        <h4 v-if="showDragMe">Drag me!</h4>
        <div v-if="showChair" class="showChairWrapp">Chair</div>
      </div>
    </div>
    {{ positions.clientX }}
  </div>
</template>

<script>
export default {
  name: 'AppDemo',
  data: function () {
    return {
      positions: {
        clientX: undefined,
        // clientY: undefined,
        movementX: 0,
        // movementY: 0
      },
      showDragMe: true,
      showChair: false
    }
  },
  methods: {
    dragMouseDown: function (event) {
      event.preventDefault()
      this.showDragMe = false;
      // get the mouse cursor position at startup:
      this.positions.clientX = event.clientX
      // this.positions.clientY = event.clientY
      document.onmousemove = this.elementDrag
      document.onmouseup = this.closeDragElement
    },
    elementDrag: function (event) {
      event.preventDefault()
      this.positions.movementX = this.positions.clientX - event.clientX
      // this.positions.movementY = this.positions.clientY - event.clientY
      this.positions.clientX = event.clientX
      if (this.positions.clientX > 970 && this.positions.clientX < 1070 ) {
        this.showChair = true
      } else {
        this.showChair = false
      }
      // this.positions.clientY = event.clientY
      // set the element's new position:
      // this.$refs.draggableContainer.style.top = (this.$refs.draggableContainer.offsetTop - this.positions.movementY) + 'px'
      this.$refs.draggableContainer.style.left = (this.$refs.draggableContainer.offsetLeft - this.positions.movementX) + 'px'
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
    background: url('../assets/bg.jpg') no-repeat left center;
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