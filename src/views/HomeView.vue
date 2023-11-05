<template>
  <div class="home">
    <section>
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-6 dark-overlay split-screen-column align-items-center align-items-lg-end" style="background-image: url(https://d19m59y37dris4.cloudfront.net/sell/2-0/img/photo/ian-dooley-347942-unsplash.jpg); background-color: #d2cecb;"> 
            <div class="overlay-content py-6 mt-6 px-lg-5 mt-lg-0 mb-lg-5">
              <h1 class="display-3 mb-4 text-white fw-bold split-screen-heading letter-spacing-1">Gentlemen              </h1>
              <p class="lead mb-4">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
              <p> <a class="btn btn-light mx-1 mb-1" href="category.html">View collection      </a><a class="btn btn-outline-light mx-1 mb-1" href="category.html">See more      </a></p>
            </div>
          </div>
          <div class="col-lg-6 split-screen-column align-items-center align-items-lg-end" style="background-image: url(https://d19m59y37dris4.cloudfront.net/sell/2-0/img/photo/ian-dooley-347962-unsplash.jpg); background-color: #e5b6b4;"> 
            <div class="py-6 px-lg-5 mb-lg-5">
              <h1 class="display-3 mb-4 text-white fw-bold split-screen-heading letter-spacing-1">Ladies              </h1>
              <p class="lead mb-4">Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
              <p> <a class="btn btn-light mx-1 mb-1" href="category.html">View collection      </a><a class="btn btn-outline-light mx-1 mb-1" href="category.html">See more                              </a></p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="pt-6 pb-5">
      <div class="container">
        <div class="row">
          <div class="col-xl-8 mx-auto text-center mb-5">
            <h2 class="text-uppercase">Nuevos Productos</h2>
          </div>
        </div>
        <div class="row">
          <!-- product-->
          <div class="col-lg-3 col-md-4 col-6" v-for="item in nuevos_productos">
            <div class="product">
              <div class="product-image">
                <div class="ribbon ribbon-danger" v-if="item.descuento">Fresh</div>
                <img class="img-fluid" :src="$url+'/obtener_portada_producto/'+item.portada" alt="product"/>
                <div class="product-hover-overlay">
                  <a class="product-hover-overlay-link" href="detail.html"></a>                 
                </div>
              </div>
              <div class="py-2">
                <p class="text-muted text-sm mb-1">{{item.categoria}}</p>
                <h3 class="h6 text-uppercase mb-1">
                  <a class="text-dark" href="detail.html">{{item.titulo}}</a>
                </h3>
                <span class="text-muted">{{convertCurrency(item.precio)}}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="py-6 bg-gray-100">
      <div class="container">
        <div class="row">
          <div class="col-xl-8 mx-auto text-center mb-5">
            <h2>Nueva colección</h2>
            <p class="lead text-muted">Esta es nuestra colección de productos de inicio, grandes ofertas por el lanzamiento de nuestro ecommerce</p>
          </div>
        </div>
        <div class="row">
          <div class="col-md-6 d-flex align-items-md-stretch mb-4 mb-md-0">
            <div class="d-flex align-items-center text-white dark-overlay w-100 text-center py-6 py-md-0" style="background: center center url(https://d19m59y37dris4.cloudfront.net/sell/2-0/img/photo/nordwood-themes-481980-unsplash-square.jpg) no-repeat; background-size: cover;"><a class="tile-link" href="category.html"> </a>
              <div class="card-img-overlay w-100 overlay-content">
                <h2 class="display-2 fw-bold text-uppercase mb-0" style="font-size: 80px;">Perifericos </h2>
              </div>
            </div>
          </div>
          <div class="col-md-6">
            <div class="card border-0 text-white text-center mb-4 dark-overlay"> <img class="card-img" src="https://d19m59y37dris4.cloudfront.net/sell/2-0/img/photo/malvestida-magazine-458585-unsplash.jpg" alt="Ladies"><a class="tile-link" href="category.html"> </a>
              <div class="card-img-overlay d-flex align-items-center">
                <div class="text-center w-100 overlay-content">
                  <h2 class="display-4 fw-bold text-uppercase text-center mb-0">Smartphones</h2>
                </div>
              </div>
            </div>
            <div class="card border-0 text-white text-center  dark-overlay"> <img class="card-img" src="https://d19m59y37dris4.cloudfront.net/sell/2-0/img/photo/heather-schwartz-528936-unsplash.jpg" alt="Accessories"><a class="tile-link" href="category.html"> </a>
              <div class="card-img-overlay d-flex align-items-center">
                <div class="text-center w-100 overlay-content">
                  <h2 class="display-4 fw-bold text-uppercase text-center mb-0">Componentes</h2>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="pt-6 pb-5">
      <div class="container">
        <div class="row">
          <div class="col-xl-8 mx-auto text-center mb-5">
            <h2 class="text-uppercase">Productos Recomendados</h2>
          </div>
        </div>
        <div class="row">
          <!-- product-->
          <div class="col-lg-3 col-md-4 col-6" v-for="item in shuffleArray(productos_recomendados)">
            <div class="product">
              <div class="product-image">
                <div class="ribbon ribbon-danger" v-if="item.descuento">Fresh</div>
                <img class="img-fluid" :src="$url+'/obtener_portada_producto/'+item.portada" alt="product"/>
                <div class="product-hover-overlay">
                  <a class="product-hover-overlay-link" href="detail.html"></a>                 
                </div>
              </div>
              <div class="py-2">
                <p class="text-muted text-sm mb-1">{{item.categoria}}</p>
                <h3 class="h6 text-uppercase mb-1">
                  <a class="text-dark" href="detail.html">{{item.titulo}}</a>
                </h3>
                <span class="text-muted">{{convertCurrency(item.precio)}}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="bg-danger">
      <div class="container">
        <div class="row">
          <div class="col-lg-6 text-white text-center py-7">
            <h2 class="display-4 text-uppercase mb-4">DESCUENTOS NAVIDEÑOS</h2>
            <p class="mb-0">Hasta</p>
            <h2 class="display-1 fw-bold mb-3">70%</h2>
            <p class="mb-5">Descuentos gratuitos para compras superiores a 100.000 COP.</p>
            <p><a class="btn btn-outline-light" href="#">Shop now</a></p>
          </div>
          <div class="col-lg-6" style="background: right bottom url(https://i.imgur.com/Rbsq6ZD.jpg) no-repeat; background-size: contain;"></div>
        </div>
      </div>
    </section>
  </div>
</template>
<style>
.product-image{
  display:block;
  overflow: hidden;
  height: 320px;
}

.img-fluid{
  height: auto !important;
  display: block !important;
}

</style>
<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import axios from 'axios';
import currency_formater from 'currency-formatter';
import {init_carrusel} from '../../public/assets/js/theme.d7b4a888';
export default {
  name: 'HomeView',
  data(){
    return { 
      nuevos_productos: [],
      productos_recomendados: [],
      load_productos_recomendados: true,
    }
  },
  methods: {
    init_nuevos_productos(){
      axios.get(this.$url+'/obtener_nuevos_productos',{
        headers: {
          'Content-Type': 'application/json'
        }
      }).then((result) => {
        this.nuevos_productos = result.data;
      }).catch((error) => {
        console.log(error);
      });
    },
    convertCurrency(mount){
            return currency_formater.format(mount, { code: 'COP' });
    },
    init_productos_recomendados(){
      axios.get(this.$url+'/obtener_productos_recomendados',{
        headers: {
          'Content-Type': 'application/json'
        }
      }).then((result) => {
        this.productos_recomendados = result.data;
        this.load_productos_recomendados = false;
        console.log(this.productos_recomendados);
      }).catch((error) => {
        console.log(error);
      });
    },
    shuffleArray(array){
      for (let i = array.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [array[i], array[j]] = [array[j], array[i]];
      } 
      return array;
    }
  },
  components: {
    HelloWorld
  },
  beforeMount(){
    init_carrusel.init();
    this.init_nuevos_productos();
    this.init_productos_recomendados();
  }
}
</script>
