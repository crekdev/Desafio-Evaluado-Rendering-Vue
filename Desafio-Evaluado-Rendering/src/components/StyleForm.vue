<script>
export default {
  name: 'StyleForm',
  data() {
    return {
      colorBackground: '',
      colorText: '',
      showText: '',
      font: ['normal', 'Georgia', 'monospace', 'sans-serif', 'serif', 'cursive', 'system-ui', 'emoji', 'fantasy'],
      typeFont: '',
      bordeRadio: '',
      contentText: '',
      blur: false,
      textSize: ''
    }
  }
}
</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col-12 col-md-6 bg-dark text-white py-3 border border-success rounded">
        <h2>Ingresa tus variables</h2>
        <div class="mb-3">
          <label for="colorBackground" class="form-label">Color de fondo</label>
          <input type="color" class="form-control form-control-color" id="colorBackground" value=""
            title="Choose your color" v-model="colorBackground">
        </div>

        <div class="mb-3">
          <label for="colorText" class="form-label">Color de texto</label>
          <input type="color" class="form-control form-control-color" id="colorText" value="" title="Choose your color"
            v-model="colorText">
        </div>

        <div class="form-check">
          <input class="form-check-input" type="checkbox" value="" id="showText" v-model="showText">
          <label class="form-check-label" for="showText">
            Mostrar texto
          </label>
        </div>

        <div>
          <label for="bordeRadio" class="form-label">Borde</label>
          <input type="range" class="form-range" min="0" max="50" id="bordeRadio" v-model="bordeRadio">
        </div>

        <div class="input-group mb-3">
          <span class="input-group-text" id="contentText">Contenido textual</span>
          <textarea class="form-control" aria-label="With textarea" v-model="contentText"></textarea>
        </div>

        <div class="mb-3">
          <label for="font">Tipografía</label>
          <select class="form-select" aria-label="Default select example" id="font" v-model="typeFont">
            <option v-for="(font, index) in font" :key="index" :value="font">
              {{ font }}
            </option>
          </select>
        </div>

        <div class="form-check mb-3">
          <input class="form-check-input" type="checkbox" value="" id="blur" v-model="blur">
          <label class="form-check-label" for="blur">
            Opaco
          </label>
        </div>

        <div class="mb-3">
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="inlineRadioOptions" id="Pequeño" value="Pequeño"
              v-model="textSize">
            <label class="form-check-label" for="Pequeño">Pequeño</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="inlineRadioOptions" id="Mediano" value="Mediano"
              v-model="textSize">
            <label class="form-check-label" for="Mediano">Mediano</label>
          </div>
          <div class="form-check form-check-inline">
            <input class="form-check-input" type="radio" name="inlineRadioOptions" id="Grande" value="Grande"
              v-model="textSize">
            <label class="form-check-label" for="Grande">Grande</label>
          </div>
        </div>
      </div>

      <div class="col-12 col-md-6 d-flex justify-content-center">
        <section v-show="colorBackground || (colorText && showText)">
          <div class="box" :style="{
            backgroundColor: colorBackground,
            color: colorText,
            borderRadius: bordeRadio + '%',
            fontFamily: typeFont,
            fontSize: textSize === 'Pequeño' ? '25px' : textSize === 'Mediano' ? '40px' : '60px'
          }" :class="{ blur: blur }">
            <p v-show="showText" class="text-center">{{ contentText }}</p>
          </div>
        </section>

      </div>
    </div>
  </div>
</template>

<style scoped>
.box {
  width: 25rem;
  height: 25rem;
  place-content: center;
}

.blur {
  opacity: 0.5;
}
</style>