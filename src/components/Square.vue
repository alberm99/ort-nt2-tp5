<template>
  <div :style="square" @click="click()"></div>
</template>

<script>

  export default  {
    name: 'src-components-square',
    props: ['index','square', 'fsquare', 'mensajes', 'fmensajes' , 'pickedColor' , 'setAllColorsTo'],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {
      click(){
        if (this.square.backgroundColor === this.pickedColor) {
          this.fmensajes.messageDisplay("You Picked Right!");
          this.setAllColorsTo(this.pickedColor);
          this.fmensajes.restartButton("Play Again!");
          this.fmensajes.headerColor(this.pickedColor);
        } else {
          this.fsquare.backgroundColor(this.index,"#232323");
          this.fmensajes.messageDisplay("Try Again!");
        }
      }
    },
    computed: {
    }
  }
</script>

<style scoped lang="css">

</style>
