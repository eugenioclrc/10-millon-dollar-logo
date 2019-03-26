<template>
  <div id="app" class="container">
    <div class="row">
      <div class="logo" style="margin:auto ;padding:40px; border: 2px solid #666; font-family: 'Varela Round', sans-serif;">
      <div class="row align-items-end text-center" style="
        margin:auto;
        border-radius: 50%;
        width: 200px;
        height: 200px;
        " :style="{ background: colorFondo }">
        <div class="col" style="font-size: 70px; font-weight: bolder" :style="{ color: colorInicial }">{{inicial}}</div>
      </div>
      <div style="font-size: 41px; font-weight: bold;" :style="{ color: colorTexto }">{{texto}}</div>
    </div>
  </div>
  <hr />
      <form>
        <div class="d-flex justify-content-center bd-highlight mb-3">
          <div class="col-md-4">
            <div class="form-inline">
    					<label class="col-sm-4 control-label">Color de fondo</label>
    					<div class="col-sm-8">
    						<colorpicker :color="colorFondo" v-model="colorFondo" />
    					</div>
    				</div>
    			</div>
          <div class="col-md-4">
            <div class="form-inline">
    					<label class="col-sm-4 control-label">Color de inicial</label>
    					<div class="col-sm-8">
    						<colorpicker :color="colorInicial" v-model="colorInicial" />
    					</div>
    				</div>
    			</div>
          <div class="col-md-4">
            <div class="form-inline">
    					<label class="col-sm-4 control-label">Color de texto</label>
    					<div class="col-sm-8">
    						<colorpicker :color="colorTexto" v-model="colorTexto" />
    					</div>
    				</div>
    			</div>
    		</div>
        <div class="d-flex justify-content-center bd-highlight mb-3">
          <div class="input-group mb-3">
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">Inicial</span>
            </div>
            <input type="text" class="form-control" v-model="inicial">
          </div>
          <div class="input-group mb-3">
            <div class="input-group-prepend">
              <span class="input-group-text" id="basic-addon1">Texto</span>
            </div>
            <input type="text" class="form-control" v-model="texto">
          </div>
        </div>
        <button type="button" class="btn btn-primary btn-large" @click="download">Descargar</button>
      </form>
      <hr />
      <h1>Crea tu logo y volvete millonario</h1>
      <ul class="list-group">
        <li class="list-group-item">
          <a target="_blank" href="https://nuestracordoba.com.ar/argentina-tiene-nuevo-logo-y-costo-10-millones/">
            Argentina tiene nuevo logo y costó $10 millones
          </a>
        </li>
        <li class="list-group-item">
          <a target="_blank" href="https://www.infobae.com/economia/2018/04/29/como-se-hizo-cuanto-costo-y-que-opinan-los-expertos-sobre-la-nueva-marca-pais/">
            Cómo se hizo, cuánto costó y qué opinan los expertos sobre la nueva Marca País
          </a>
        </li>
        <li class="list-group-item">
          <a target="_blank" href="https://www.eldisenso.com/breves/el-gobierno-pago-mas-de-10-millones-de-pesos-por-el-nuevo-logo-de-argentina/">
          El gobierno pagó más de 10 millones de pesos por el nuevo logo de Argentina
        </a></li>
        <li class="list-group-item">
          <a target="_blank" href="http://www.enorsai.com.ar/politica/24651-en-pleno-ajuste--el-gobierno-gasto-10-millones-en-un-logo.html">
          En pleno ajuste, el Gobierno gastó $10 millones en un logo
        </a></li>
        <li class="list-group-item">
          <a target="_blank" href="https://extrabaires.info/el-gobierno-nacional-pago-mas-de-10-millones-de-pesos-por-un-logo/">
          El gobierno nacional pagó más de 10 millones de pesos por un logo
        </a></li>
        <li class="list-group-item">
          <a target="_blank" href="https://mundoempresarial.com.ar/noticia/710/nueva-marca-pais-los-secretos-de-un-diseno-de-10-millones-de-pesos">
          Nueva Marca País: los secretos de un diseño de 10 millones de pesos
        </a></li>
        <li class="list-group-item">
          <a target="_blank" href="http://diariosinfiltro.com/mauricio-macri-pago-10-millones-de-pesos-por-el-diseno-del-nuevo-logo-de-argentina/">
          MAURICIO MACRI PAGÓ 10 MILLONES DE PESOS POR EL DISEÑO DEL NUEVO LOGO DE ARGENTINA
        </a></li>
      </ul>
      <hr />
  </div>
</template>

<script>
import html2canvas from 'html2canvas';
import colorpicker from './components/colorpicker.vue';

export default {
  components: {
    colorpicker,
  },
  name: 'app',
  data() {
    return {
      colorInicial: '#fff',
      inicial: 'A',
      colorFondo: '#3fa7e1',
      texto: 'Argentina',
      colorTexto: '#3fa7e1',
    };
  },
  methods: {
    download() {
      html2canvas(document.querySelector('.logo'))
      .then((canvas) => {
        const myImage = canvas.toDataURL();
        const link = document.createElement("a");

        link.download = "logo.png";
        link.href = myImage;
        document.body.appendChild(link);
        link.click();
      });
    },
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
