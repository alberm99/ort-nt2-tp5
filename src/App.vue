<template>
  <Encabezado 
    :color="mensajes.headerColor"
    :color-display="colorDisplay"
  />
  <Navigator 
    :reset="restartButton"
    :easy="easy"
    :hard="hard"
    :msg-button= "mensajes.restartButton"
    :message-display= "mensajes.messageDisplay"
    :is-hard="isHard"
  />
  <Container 
    :fmensajes="fmensajes"
    :mensajes="mensajes"
    :squares="squares"
    :fsquare="fsquare"
    :set-all-colors-to="setAllColorsTo"
    :picked-color="pickedColor"
  />
</template>

<script>
import Encabezado from './components/Encabezado.vue'
import Navigator from './components/Navigator.vue'
import Container from './components/Container.vue'

export default {
  name: 'App',
  components: {
    Encabezado
    ,Navigator
    ,Container
  }
  ,mounted(){
		this.init()
	}
  ,data () {
    return {
      colorCount : 6
      ,isHard: true
      ,colors: []
      ,squares : []
      ,mensajes: {
        messageDisplay:''
        ,restartButton:''
        ,headerColor:''
      }
      ,pickedColor : 'RBG'
      ,colorDisplay:''

      ,fmensajes : {
				headerColor : this.setHeaderColor,
				messageDisplay: this.setMessageDisplay,
				restartButton: this.setRestartButton
			},
			fsquare : {
				backgroundColor : this.setBackgroundColor
			}
    }
  },

  methods:{

    setHeaderColor(color) {
			this.mensajes.headerColor = color
		},

		setMessageDisplay(mensaje) {
			this.mensajes.messageDisplay = mensaje
		},

		setRestartButton(mensaje) {
			this.mensajes.restartButton = mensaje
		},

		setBackgroundColor(index, color) {
			this.squares[index] = {backgroundColor:color}
		},

		restart(){
			this.colors = this.createNewColors(this.colorCount);
			this.pickedColor = this.colors[this.PickColor()];
			this.colorDisplay = this.pickedColor;
			this.mensajes.headerColor = "steelblue";
			this.mensajes.messageDisplay = "";
			this.mensajes.restartButton = "New Colors!";
			for (var i = 0; i <this.squares.length; i++) {
				this.squares[i].backgroundColor = this.colors[i];
			}

		},


		restartButton(){
			this.restart()
		},
		
		init(){
			for (var i = 0; i < 6; i++) {
				this.squares.push({
					display: 'block',
					backgroundColor: ''
				})
			}
			this.restart()
		},
		
		easy(){
			if(this.isHard){
				this.isHard = false
				this.colorCount = 3
				for(var i =0; i < this.colorCount; i++){
					this.squares[(i+3)].display = 'none'
				}
				this.restart()
			}
		},
		

		hard(){
			if(!this.isHard){
				this.isHard = true
				this.colorCount = 6
				this.restart()
				for(var i =0; i < this.colorCount; i++){
					this.squares[i].display = 'block'
				}

			}
		}

		
		,setAllColorsTo(color) {
			this.squares.forEach((square) => {
				square.backgroundColor = color;
			})
		},
		
		PickColor(){
			var quantity;
			if (this.isHard) {
				quantity = 6;
			} else {
				quantity = 3;
			}
			return Math.floor(Math.random() * quantity );
    },
    
		createNewColors(numbers){
			var arr = [];
			for (var i = 0; i < numbers; i++) {
				arr.push(this.createRandomStringColor());
			}
			return arr;
		},
		
		createRandomStringColor(){
			var newColor = "rgb(" + this.randomInt() + ", " + this.randomInt() + ", " + this.randomInt() + ")" ;
		//	console.log(newColor);
		return newColor;
    },
    
		randomInt(){
			return Math.floor(Math.random() * 256);
		}
	}
}
</script>

<style>
#app {
}
body {
	background: #232323;
	margin: 0;
	font-family: "Montserrat", "Avenir";
}

h1 {
	font-weight: normal;
	line-height: 1.1;
	padding: 20px 0;

}
#navigator {

	background: #ffffff;
	height: 30px;
	text-align: center;
	margin: 0;
	margin-top: -30px;

}
#header {
	transition: all 0.3s;
	background: steelblue;
	text-transform: uppercase;
	text-align: center;
	margin: 0;
	color: white;
	
}
#colorDisplay {
	font-size: 200%;
}


.square {
	width: 30%;
	background: blue;
	padding-bottom: 30%;
	float: left;
	margin: 1.66%;
	border-radius: 10%;
	transition: background 0.8s;
	-webkit-transition: background 0.8s;
	-moz-transition: background 0.8s;

}
#container {
	margin: 20px auto;
	max-width: 600px;
}
#message {
	color: #ffffff;
	display: inline-block;
	width: 20%;
}

#messageBox {
	
}
.selected {
	background-color: steelblue;
	color: white;
}
button {
	border: none;
	background-color: white;
	font-family: "Montserrat", "Avenir";
	text-transform: uppercase;
	height: 100%;
	font-weight: 700;
	letter-spacing: 1px;
	color: steelblue;
	transition: all 0.3s;
	outline: none;
}
button:hover {
	color: white;
	background-color: steelblue;
}
</style>
