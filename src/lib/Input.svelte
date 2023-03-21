<script>
  import {queryGlobal} from "../store/stores";
  let valueInput = "";

  const handleInput = (e) => {
    if(e.key == "Enter"){
      if(e.target.value[e.target.value.length -1]=="?")
      {
        changequery("¿" + e.target.value)
      }
      else{
        changequery(`Recuerda usar el signo "?"`)
      }
    }
    
  }
  const changequery = (change) => {
    queryUpdate(change)
    valueInput=""
  }

  const queryUpdate =(value)=> {
    queryGlobal.update(() => value)
    
  }
</script>

<div class="text-center">
  <h3 class="text-3xl mt-4">Inserta tu pregunta</h3>
  <input bind:value={valueInput} on:keydown={(e)=> {handleInput(e)}} type="text" placeholder="Voy hacer millonario?" class="mt-5 input input-bordered shadow-md input-primary w-full max-w-xs" />
  <h4 class="text-base font-bold mt-3">Tu pregunta debe terminar con el "?"</h4>
</div>
