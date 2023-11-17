<template>
  <footer class="main-footer">
    <!-- Services block-->
    <div class="bg-black-100 text-dark-700 py-6">
      <div class="container">
        <div class="row">
          <div class="col-lg-4 service-column">
            <!-- <svg >
              <use xlink:href="#delivery-time-1"> </use>
            </svg> -->
            <img class="svg-icon service-icon" src="/assets/media/camion.gif" alt="">
            <div class="service-text">
              <h6 class="text-uppercase">Envío gratuito &amp; devoluciones</h6>
              <p class="text-muted fw-light text-sm mb-0">Envío gratuito para compras superiores a $200.000 COP</p>
            </div>
          </div>
          <div class="col-lg-4 service-column">
            <img class="svg-icon service-icon" src="/assets/media/euro.gif" alt="">
            <div class="service-text">
              <h6 class="text-uppercase">Garantía de devolución de dinero</h6>
              <p class="text-muted fw-light text-sm mb-0">30 días de garantia de devolución</p>
            </div>
          </div>
          <div class="col-lg-4 service-column">
            <img class="svg-icon service-icon" src="/assets/media/tailandes.gif" alt="">
            <div class="service-text">
              <h6 class="text-uppercase">020-800-4567</h6>
              <p class="text-muted fw-light text-sm mb-0">24/7 Soporte Disponible en Línea</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Main block - menus, subscribe form-->
    <div class="py-6 bg-gray-300 text-muted"> 
      <div class="container">
        <div class="row">
          <div class="col-lg-4 mb-5 mb-lg-0">
            <div class="fw-bold text-uppercase text-lg text-dark mb-3">SELL<span class="text-primary">: A Shimada Tech Company</span></div>
            <p>I need healing.</p>
            <ul class="list-inline">
              <li class="list-inline-item">
                <a class="text-muted text-primary-hover" href="#" target="_blank" title="twitter"></a>
                <img src="/assets/media/facebook.png" style="width: 18px;">
              </li>
              <li class="list-inline-item">
                <a class="text-muted text-primary-hover" href="#" target="_blank" title="facebook"></a>
                <img src="/assets/media/whatsapp.png" style="width: 18px;">
              </li>
              <li class="list-inline-item">
                <a class="text-muted text-primary-hover" href="#" target="_blank" title="instagram"></a>
                <img src="/assets/media/twitter-alt.png" style="width: 18px;">
              </li>
              <li class="list-inline-item">
                <a class="text-muted text-primary-hover" href="#" target="_blank" title="pinterest"></a>
                <img src="/assets/media/instagram.png" style="width: 18px;">
              </li>
            </ul>
          </div>
          <div class="col-lg-2 col-md-6 mb-5 mb-lg-0">
            <h6 class="text-uppercase text-dark mb-3">Categorías</h6>
            <ul class="list-unstyled">
              <li> <a class="text-muted" href="#">Celulares</a></li>
              <li> <a class="text-muted" href="#">Periféricos</a></li>
              <li> <a class="text-muted" href="#">Componentes</a></li>
              <li> <a class="text-muted" href="#">IoT</a></li>
              <li> <router-link :to="{name: 'shop'}" class="text-muted">Toda la tienda</router-link></li>
            </ul>
          </div>
          <div class="col-lg-2 col-md-6 mb-5 mb-lg-0">
            <h6 class="text-uppercase text-dark mb-3">Usuario</h6>
            <ul class="list-unstyled">
              <li> <router-link :to="{name: 'login'}" class="text-muted">Iniciar Sesión</router-link></li>
              <li> <router-link :to="{name: 'login'}" class="text-muted">Regístrate</router-link></li>
              <li> <a class="text-muted" href="#">Tus compras                   </a></li>
            </ul>
          </div>
          <div class="col-lg-4">
            <h6 class="text-uppercase text-dark mb-3">Boletín informativo</h6>
            <p class="mb-3"> Suscríbete a nuestro boletín informativo para recibir nuestras ofertas y lo último en noticias relacionadas con nuestra tienda.</p>
            <form action="#" id="newsletter-form">
              <div class="input-group mb-3">
                <input class="form-control bg-transparent border-secondary border-end-0" type="email" placeholder="Tu correo electrónico... " aria-label="Your Email Address" style >
                <div class="input-group-append">
                  <button class="btn border-secondary border-start-0" type="submit" style="border-color: black;"><img src="/assets/media/avion-de-papel.png" style="width: 18px;"></button>
                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
    <!-- Copyright section of the footer-->
    <div class="py-4 fw-light bg-gray-800 text-gray-300">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-md-6 text-center text-md-start">
            <p class="mb-md-0">&copy; {{year}} Daniel García, Carolina Tobón, Johnny Paz.  Todos los derechos reservados.</p>
          </div>
          <div class="col-md-6">
            <ul class="list-inline mb-0 mt-2 mt-md-0 text-center text-md-end">
              <li class="list-inline-item"><img class="w-2rem" src="https://d19m59y37dris4.cloudfront.net/sell/2-0/img/visa.svg" alt="..."></li>
              <li class="list-inline-item"><img class="w-2rem" src="https://d19m59y37dris4.cloudfront.net/sell/2-0/img/mastercard.svg" alt="..."></li>
              <li class="list-inline-item"><img class="w-2rem" src="https://d19m59y37dris4.cloudfront.net/sell/2-0/img/paypal.svg" alt="..."></li>
              <li class="list-inline-item"><img class="w-2rem" src="https://d19m59y37dris4.cloudfront.net/sell/2-0/img/western-union.svg" alt="..."></li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  data(){
    return {
      year: new Date().getFullYear(),
    }
  }
}
</script> 
  