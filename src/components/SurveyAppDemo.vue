<template>
  <div class="wrapper">
    <div class="sliding-bg">
      <div ref="draggableContainer" id="draggable-container" @mousedown="dragMouseDown">
        <img name="phone" class="phone" src="../assets/ShyftX_hand.png" alt="phone" />
        <h4 v-if="showDragMe">Drag me!</h4>
        <div v-if="showChair" class="showChairWrapp">Chair</div>
      </div>
    </div>
    {{ positionX }}
    <br>
    {{ movementX }}
    <br>


  </div>
</template>

<script>
export default {
  name: 'AppDemo',
  data: function () {
    return {
      positionX: undefined,
      movementX: 0,
      showDragMe: true,
      showChair: false,

    }
  },
  methods: {
    dragMouseDown: function (event) {
      event.preventDefault()
      this.showDragMe = false;
      // get the mouse cursor position at startup:
      this.positionX = event.clientX

      document.onmousemove = this.elementDrag
      document.onmouseup = this.closeDragElement
    },
    elementDrag: function (event) {
      event.preventDefault()
      this.movementX = this.positionX - event.clientX
      this.positionX = event.clientX
      console.log(this.movementX)

      // if (this.positions.clientX > 970 && this.positions.clientX < 1070 ) {
      //   this.showChair = true
      // } else {
      //   this.showChair = false
      // }
      
      // this.positions.clientY = event.clientY
      // set the element's new position:
      this.$refs.draggableContainer.style.left = (this.$refs.draggableContainer.offsetLeft - this.movementX) + 'px'

    },
    closeDragElement () {
      document.onmouseup = null;
      document.onmousemove = null;
      this.showDragMe = true;
      this.showChair = false;
    },
    convertPXToVW: function(px) {
      if(px > 0) {
        return px * (100 / document.documentElement.clientWidth);
      } else if (px < 0) {
        return -Math.abs(px * (100 / document.documentElement.clientWidth));
      } else {
        return 0
      }
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
  }
  .sliding-bg {
    position: relative;
    background: url('../assets/ShyftX_room.jpg') no-repeat left center;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
    width: 100vw;
    max-width:100%;
    height: 30vw;
    animation: slide 60s linear infinite;
  }
  .phone {
    width: 67vw;
    vertical-align: bottom;
  }
  #draggable-container {
    position: absolute;
    bottom: 0;
    width: 67vw;
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