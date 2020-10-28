<template>

  <section class="src-components-headerColors">
		<div id="header" :style="{backgroundColor: color}">
		  <h1>The Great <br>
		  	<span id="colorDisplay">{{colorDisplay}}</span>
			  <br>
			  Guessing Game
      </h1>
		</div>
	
  </section>

</template>

<script>

  export default  {
    name: 'src-components-headerColors',
    props: ['color','colorDisplay'],
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
