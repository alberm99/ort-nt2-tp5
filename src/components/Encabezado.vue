<template>
  <div id="header" :style="{backgroundColor: color}">
    <h1>The Great 
      <br>
      <span id="colorDisplay">{{colorDisplay}}</span>
      <br>
      Guessing Game
    </h1>
  </div>
</template>

<script>

  export default  {
    name: 'src-components-encabezado',
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
