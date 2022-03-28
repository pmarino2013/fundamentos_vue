<template>
  <h2>{{customTitle}}</h2>
  <p>{{counter}} <sup>{{exponente}}</sup> = {{powCounter}} </p>
  <div>
  <button @click="ingrease">+1</button>
  <button @click="decrease">-1</button>


  </div>
  
 

</template>

<script>
export default {
props:{
    title:String,
    start:{
        type:Number,
        default:100,
        validator(value){
            return value >= 0
        }
        // required:true,
    }
},
data(){
    return{
        counter:this.start,
        exponente:2
    }
},
methods:{
    ingrease(){
         this.counter++
    },
    decrease(){
        this.counter--
    }
},
computed:{
    //La ventaja sobre funciones es que guarda el valor en cache de esa manera solo se ejecutará otra vez si cambia el valor de counter
    powCounter(){
        // console.log('Computed powCounter')
        return Math.pow(this.counter,this.exponente)
    },
    customTitle(){
        return this.title ? this.title : 'Counter'
    }

}
}
</script>

<style>
button{
    background-color: #64b687;
    border-radius: 5px;
    border: 1px solid white;
    color:white;
    cursor:pointer;
    margin: 0 5px;
    padding:5px 15px;
    transition: 0.3s ease-in-out;
}

button:hover{
    background-color: #5aa67b;
    transition: 0.3s ease-in-out;
}
</style>