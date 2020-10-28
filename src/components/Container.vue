<template>
  <section class="src-components-container">
    <div id="container">
			<Square 
				class="square" 
        :index="index"
				:fmensajes="fmensajes"
				:mensajes="mensajes"
				:square="square"
				:fsquare="fsquare"
				:set-all-colors-to="setAllColorsTo"
				:picked-color="pickedColor"
				v-for="(square,index) in squares"
				:key="index"
			></Square>
		</div>
  </section>

</template>

<script>
import Square from './Square.vue'

  export default  {
    name: 'src-components-container',
    components:{
      Square
    },
    props: ['mensajes', 'fmensajes','setAllColorsTo','pickedColor','squares', 'fsquare'],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">


</style>
