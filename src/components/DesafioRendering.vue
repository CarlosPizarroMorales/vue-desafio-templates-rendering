<template>
  <main> 
    <form @submit.prevent>
      <label>Color de fondo:
        <input v-model="bgColor" type="text">
      </label>
      
      <label>Color de texto:
        <input v-model="fontColor" type="text">
      </label>
      
      <label class="row">Mostrar texto:
        <input v-model="isVisible" type="checkbox">
      </label>
      
      <label>Borde: {{ border }}
        <input :data-value="border" v-model="border" type="range" min="1" max="50" step="1" value="1">
      </label>

      <label>Contenido textual:
        <textarea v-model="textContent" cols="30" rows="3" maxlength="150"></textarea>
      </label>
      
      <label>Tipografía:
        <select v-model="fontFamily">
          <option value="Arial" selected disabled>Elija una opción:</option>
          <option v-for="font in fonts" :key="font" :value="font">{{ font }}</option>
        </select>
      </label>
      
      <label class="row">Opaco:
        <input disabled v-model="isTransparentContent" type="checkbox">
      </label>
      
      <fieldset class="row">
        <legend>Tamaño de letra</legend>
        <label class="row">
          <input checked v-model="fontSize" type="radio" name="fontSize" value="font-sm">
          Pequeño
        </label>
        
        <label class="row">
          <input v-model="fontSize" type="radio" name="fontSize" value="font-md">
          Mediano
        </label>
        
        <label class="row">
          <input v-model="fontSize" type="radio" name="fontSize" value="font-xl">
          Grande
        </label>
      </fieldset>
    </form>

    <section :style="{ backgroundColor: bgColor, border: border + 'px groove silver'  }">
      <p :class="fontSize" v-show="isVisible" :style="{ color: fontColor, fontFamily: fontFamily }">{{ textContent }}</p>
    </section>  
  </main>
</template>

<script>

export default {
  name: "DesafioRendering",
  data(){
    return {
      bgColor: '',
      fontColor: '',
      isVisible: '',
      border: '',
      textContent: '',
      fontFamily: '',
      fonts: ['cursive', 'monospace'],
      isTransparentContent: '',
      fontSize: '',
    }
  }
}
</script>


<style scoped>
  main {
    display: flex;
    align-items: stretch;
    justify-content: space-between;
    gap: 2rem;
    padding: 5rem;
    width: 70vw;
    margin: 0 auto;
  }

  main > form,
  main > section {
    flex: 1;
    border-radius: 16px;
  }
  form {
    background-color: #2f4f4f;
    color: #ffffff;
    padding: 2rem;
    display: flex;
    flex-direction: column;

    & > label,
    & > fieldset {
      display: flex;
      flex-direction: column;
      margin-top: 1rem;
    }

    input[type="checkbox"] {
      scale: 1.5;
      margin-left: 0.5rem;
    }

    .row {
      flex-direction: row;
    }

    & * {
      outline: blue;      
    }
  }

  section {
    width: 300px;
    height: auto;
    padding: 1rem 2rem;
    /* box-sizing: border-box !important; */
    
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: auto;

    color: white;
  }

  .font-sm {
    font-size: 1rem;
    font-weight: 400;
  }
  
  .font-md {
    font-size: 1.25rem;
    font-weight: 500;
  }
  
  .font-xl {
    font-size: 2rem;
    font-weight: 700;
  }

  #markers option {
    background-color: white;
  }
</style>
