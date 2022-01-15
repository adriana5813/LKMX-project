<template>
  <center><li>
    <input v-model="todo.text" placeholder="Tarea" class="input"> 
    <button @click.prevent="$emit('remove', todo)" id="b1" class="buton">Eliminar</button>
    <button @click.prevent="$emit('edit', todo)" id="b2" class="buton">Editar</button>
  </li></center>
</template>


<script>
export default {
  props: {
    todo: {
      required: true,
      type: Object
    }
  }
}
</script>

<style >
#b1 {background-color: #f44336;} 
#b2 {background-color: #4CAF50;}
.buton{
    color: white;
    border: none;
    margin-left:5px;
    font-size: 15px;
    border-radius: 3px;
    
}
li{
    margin-top: 5px;
    width: 100%;
    list-style-type: none;
}
input{
    width: 60%;
    text-align: left;
}


</style>


