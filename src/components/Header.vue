<template>
  <header class="header header-absolute">
    <!-- Top Bar-->
    <div class="top-bar">
      <div class="container-fluid">
        <div class="row d-flex align-items-center">
          <div class="col-sm-7 d-none d-sm-block">
            <ul class="list-inline topbar-text mb-0">
              <li class="list-inline-item pe-3 me-0">
                <img src="/assets/icons/telephone-bl.png" style="width: 16px;">
                300000000
              </li>
              <li class="list-inline-item px-3 border-start d-none d-lg-inline-block">Envios gratis desde $200.000</li>
            </ul>
          </div>
          <div class="col-sm-5 d-flex justify-content-end">
            <!-- Currency Dropdown-->
            <div class="dropdown ps-3 ms-0"><a class="dropdown-toggle topbar-link" id="currencyDropdown" href="#" data-bs-toggle="dropdown" data-bs-display="static" aria-haspopup="true" aria-expanded="false">COP</a>
              <div class="dropdown-menu dropdown-menu-end dropdown-menu-animated" aria-labelledby="currencyDropdown">
                <a class="dropdown-item text-sm" href="#"> 
                  USD
                </a>
              </div>
              
            <!-- Language Dropdown-->
            <a style="cursor:pointer" v-if="$store.state.token" v-on:click="logout()">
              <span><b>Cerrar sesión</b></span>
            </a>

            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- Top Bar End-->
      <!-- Navbar-->
      <nav class="navbar navbar-expand-lg navbar-sticky navbar-airy navbar-dark bg-fixed-white navbar-fixed-light" style="background: #2c2c2c !important;">
        <div class="container-fluid">  
          <!-- Navbar Header  -->
          <a class="navbar-brand" style="color:white !important" href="#">
    <svg class="navbar-brand-svg" viewBox="0 0 65 16" width="85" height="20" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path class="navbar-brand-svg-text" d="M5.72266 18.1562C4.88281 18.1562 4.08529 18.0033 3.33008 17.6973C2.58138 17.3913 1.94661 16.9355 1.42578 16.3301C0.911458 15.7181 0.582682 14.9759 0.439453 14.1035L2.90039 13.4785C2.98503 14.2988 3.28776 14.9173 3.80859 15.334C4.33594 15.7507 4.98698 15.959 5.76172 15.959C6.23698 15.959 6.64714 15.8841 6.99219 15.7344C7.33724 15.5781 7.59766 15.3665 7.77344 15.0996C7.94922 14.8327 8.03711 14.5332 8.03711 14.2012C8.03711 13.804 7.91341 13.4655 7.66602 13.1855C7.42513 12.9056 7.1224 12.6745 6.75781 12.4922C6.39323 12.3099 5.89193 12.0918 5.25391 11.8379C4.42057 11.5059 3.74674 11.1999 3.23242 10.9199C2.7181 10.6335 2.27539 10.2363 1.9043 9.72852C1.53971 9.2207 1.35742 8.57943 1.35742 7.80469C1.35742 7.01693 1.54948 6.33659 1.93359 5.76367C2.32422 5.18424 2.84505 4.74479 3.49609 4.44531C4.15365 4.14583 4.8763 3.99609 5.66406 3.99609C6.54948 3.99609 7.35677 4.19792 8.08594 4.60156C8.8151 4.9987 9.40755 5.60417 9.86328 6.41797L7.80273 7.67773C7.56185 7.20898 7.24609 6.84766 6.85547 6.59375C6.46484 6.33333 6.03841 6.20312 5.57617 6.20312C5.25065 6.20312 4.95443 6.26497 4.6875 6.38867C4.42708 6.51237 4.21875 6.68815 4.0625 6.91602C3.91276 7.13737 3.83789 7.39128 3.83789 7.67773C3.83789 8.0293 3.95182 8.32878 4.17969 8.57617C4.40755 8.82357 4.69401 9.0319 5.03906 9.20117C5.39062 9.37044 5.86914 9.57227 6.47461 9.80664C7.33398 10.1387 8.0306 10.4512 8.56445 10.7441C9.09831 11.0371 9.55729 11.4473 9.94141 11.9746C10.3255 12.502 10.5176 13.1693 10.5176 13.9766C10.5176 14.8229 10.3027 15.5618 9.87305 16.1934C9.44987 16.8249 8.8737 17.3099 8.14453 17.6484C7.41536 17.987 6.60807 18.1562 5.72266 18.1562ZM16.8906 4.20117H26.0703V6.47656H19.3711V9.96289H25.6113V12.2383H19.3711V15.6562H26.0703V18H16.8906V4.20117ZM33.0586 4.20117H35.5391V15.6562H41.4375V18H33.0586V4.20117ZM47.4492 4.20117H49.9297V15.6562H55.8281V18H47.4492V4.20117Z" transform="translate(0 -3)" fill="#212529"/>
        <path class="text-primary" d="M62.0254 15.4219H64.418V18H62.0254V15.4219Z" transform="translate(0 -3)" fill="#9A6EE2"/>
    </svg>
</a>

          <button class="navbar-toggler navbar-toggler-right" type="button" data-bs-toggle="collapse" data-bs-target="#navbarCollapse" aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation"><i class="fa fa-bars"></i></button>
          <!-- Navbar Collapse -->
          <div class="collapse navbar-collapse" id="navbarCollapse">
            <ul class="navbar-nav mx-auto">
              <li class="nav-item">
                <router-link to="/" class="nav-link">Inicio</router-link>
              </li>
              <li class="nav-item">
                <router-link :to="{name: 'shop'}" class="nav-link">Todos los Productos</router-link>
              </li>
              <!-- Megamenu-->
              <li class="nav-item dropdown position-static"><a class="nav-link dropdown-toggle " href="#" data-bs-toggle="dropdown">Categorías</a>
                <div class="dropdown-menu dropdown-menu-animated megamenu py-lg-0">
                  <div class="row">
                    <div class="col-lg-9">
                      <div class="row p-3 pe-lg-0 ps-lg-5 pt-lg-5">
                        <div class="col-lg-3">
                          <!-- Megamenu list-->
                          <h6 class="text-uppercase">Celulares</h6>
                          <ul class="megamenu-list list-unstyled">
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="index.html">iPhone   </a></li>
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="index2.html">Samsung   </a></li>
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="index3.html">Xiaomi   </a></li>
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="index4.html">ASUS  <span class="badge bg-warning ms-1">New</span>   </a></li>                          </ul>
                            
                          </div>
                        <div class="col-lg-3">
                        <!-- Megamenu list-->
                          <h6 class="text-uppercase">Periféricos</h6>
                          <ul class="megamenu-list list-unstyled">
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="category.html">Mouse   </a></li>
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="category-right.html">Diadema  </a></li>
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="category-no-sidebar.html">Teclado  </a></li>
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="category-no-sidebar.html">Monitor <span class="badge bg-warning ms-1">New</span>   </a></li>
                          </ul>
                        </div>
                        
                        <div class="col-lg-3">                   
                          <!-- Megamenu list-->
                          <h6 class="text-uppercase">Componentes</h6>
                          <ul class="megamenu-list list-unstyled">
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="cart.html">RAM  </a></li>
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="cart-2.html">SSD <span class="badge bg-warning ms-1">New</span>   </a></li>
                            <li class="megamenu-list-item"><a class="megamenu-list-link" href="checkout1.html">Motherboard   </a></li>
                          </ul>
                        </div>
                        <div class="col-lg-3">
                        
                        <!-- Megamenu list-->
                        <h6 class="text-uppercase">Internet of Things</h6>
                        <ul class="megamenu-list list-unstyled">
                          <li class="megamenu-list-item"><a class="megamenu-list-link" href="blog.html">Asistente de voz  </a></li>
                          <li class="megamenu-list-item"><a class="megamenu-list-link" href="post.html"> Casa Inteligente </a></li>
                        </ul>
                      </div>
                      </div>
                      <div class="row megamenu-services d-none d-lg-flex">
                        <div class="col-xl-3 col-lg-6 d-flex">
                          <div class="megamenu-services-item">
                            <svg class="svg-icon megamenu-services-icon">
                              <use xlink:href="#delivery-time-1"> </use>
                            </svg>
                            <div>
                              <h6 class="text-uppercase">Envío Gratis &amp; Devoluciones</h6>
                              <p class="mb-0 text-muted text-sm">Envío gratuito para compras superiores a $200.000 COP</p>
                            </div>
                          </div>
                        </div>
                        <div class="col-xl-3 col-lg-6 d-flex">
                          <div class="megamenu-services-item">
                            <svg class="svg-icon megamenu-services-icon">
                              <use xlink:href="#money-1"> </use>
                            </svg>
                            <div>
                              <h6 class="text-uppercase">GARANTÍA DE DEVOLUCIÓN DE DINERO</h6>
                              <p class="mb-0 text-muted text-sm">30 días de garantía de devolución</p>
                            </div>
                          </div>
                        </div>
                        <div class="col-xl-3 col-lg-6 d-flex">
                          <div class="megamenu-services-item">
                            <svg class="svg-icon megamenu-services-icon">
                              <use xlink:href="#customer-support-1"> </use>
                            </svg>
                            <div>
                              <h6 class="text-uppercase">020-800-4567</h6>
                              <p class="mb-0 text-muted text-sm">24/7 Soporte Disponible en Línea</p>
                            </div>
                          </div>
                        </div>
                        <div class="col-xl-3 col-lg-6 d-flex">
                          <div class="megamenu-services-item">
                            <svg class="svg-icon megamenu-services-icon">
                              <use xlink:href="#secure-payment-1"> </use>
                            </svg>
                
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="col-lg-3 d-none d-lg-block position-relative"><img class="bg-image" src="https://i.redd.it/1gkp6jo1b3j41.jpg" alt=""></div>
                  </div>
                </div>
              </li>
            </ul>
            <div class="d-flex align-items-center justify-content-between justify-content-lg-end mt-1 mb-2 my-lg-0">
              
                <!-- User Not Logged - link to login page-->
                <div class="nav-item">
                    <router-link v-if="!$store.state.token" class="navbar-icon-link" to="/login">
                      <img src="/assets/icons/user.png" style="width: 25px;" />
                        <span class="text-sm ms-2 ms-lg-0 text-uppercase text-sm fw-bold d-none d-sm-inline d-lg-none">Log in </span>
                    </router-link>
                    <a v-if="$store.state.token" class="navbar-icon-link dropdown">
                      <img src="/assets/icons/user.png" style="width: 25px;" />
                        <span class="text-sm ms-2 ms-lg-0 text-uppercase text-sm fw-bold d-none d-sm-inline dropdown-toggle" data-bs-target="#" data-bs-toggle="dropdown" aria-haspopup="true" aria-expanded="false"> &nbsp; {{user.nombres}} 
                        </span>
                        <div class="dropdown-menu dropdown-menu-animated" aria-labelledby="categoryDropdownMenuLink" style="    left: -40px !important;">
                            <router-link class="dropdown-item" to="/cuenta/venta">Mis compras</router-link>
                            <router-link class="dropdown-item" to="/cuenta/direcciones">Direcciones</router-link>
                            <a class="dropdown-item" v-on:click="logout()">Cerrar sesión </a>
                        </div>
                    </a>
                </div>
                <!-- Cart Dropdown-->
                <div class="nav-item dropdown">
                    <a class="navbar-icon-link d-lg-none" href="cart.html">
                        <img src="/assets/icons/user.png" style="width: 25px;" />
                        <span class="text-sm ms-2 ms-lg-0 text-uppercase text-sm fw-bold d-none d-sm-inline d-lg-none">View cart</span>
                    </a>
                    <div class="d-none d-lg-block">
                        <a class="navbar-icon-link" id="cartdetails" href="cart.html" data-bs-target="#" data-bs-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                            <img src="/assets/icons/cart.png" style="width: 25px;" />
                            <div class="navbar-icon-link-badge">{{ carrito_length }}</div>
                        </a>
                        <div class="dropdown-menu dropdown-menu-animated dropdown-menu-end p-4" aria-labelledby="cartdetails" style="max-width: 350px !important;">
                            <div class="navbar-cart-product-wrapper" style="overflow-x: hidden !important" >
                                <!-- cart item-->

                                <div class="navbar-cart-product" v-for="item in carrito">
                                    <div class="d-flex align-items-center">
                                        <a href="detail.html"><img class="img-fluid navbar-cart-product-image" :src="$url+'/obtener_portada_producto/'+item.producto.portada" alt="..." /></a>
                                        <div class="w-100">
                                            <div class="ps-3"><router-link :to="{name: 'show-product', params: {slug: item.producto.slug}}" class="navbar-cart-product-link" style="text-overflow:ellipsis;overflow: hidden;white-space: nowrap;">{{item.producto.titulo}}</router-link>
                                              <small class="d-block text-muted">{{item.producto.str_variedad}}: {{ item.variacion.variacion }}</small>
                                              <small class="d-block text-muted">Cantidad: {{item.cantidad}}</small>
                                              <strong class="d-block text-sm">{{convertCurrency(item.producto.precio * item.cantidad)}}</strong></div>
                                        </div>
                                    </div>
                                </div>
                                
                            </div>
                            <!-- total price-->
                            <div class="navbar-cart-total"><span class="text-uppercase text-muted">Total</span><strong class="text-uppercase">{{convertCurrency(total)}}</strong></div>
                            <!-- buttons-->
                            <div class="d-flex justify-content-between">
                                <router-link class="btn btn-link text-dark me-3" to="/cart">Carrito
                                  <img src="/assets/icons/shopping-bag.png" style="width: 15px;">
                                </router-link>
                                <router-link class="btn btn-outline-dark" to="/checkout">Ir a pagar</router-link>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

          </div>
        </div>
      </nav>
      <!-- /Navbar -->
      <!-- Fullscreen search area-->
      <div class="search-area-wrapper">
        <div class="search-area d-flex align-items-center justify-content-center">
          <div class="close-btn">
            <svg class="svg-icon svg-icon-light w-3rem h-3rem">
              <use xlink:href="#close-1"> </use>
            </svg>
          </div>
          <form class="search-area-form" action="#">
            <div class="mb-4 position-relative">
              <input class="search-area-input" type="search" name="search" id="search" placeholder="What are you looking for?">
              <button class="search-area-button" type="submit">
                <svg class="svg-icon">
                  <use xlink:href="#search-1"> </use>
                </svg>
              </button>
            </div>
          </form>
        </div>
      </div>
      <!-- /Fullscreen search area-->
    </header>
  </template>
  
  <script>
import { RouterLink } from 'vue-router';
import currency_formatter from 'currency-formatter';
import axios from 'axios';

  export default {
    name: 'Header',
    data() {
      return {
        user: JSON.parse(this.$store.state.user),
        carrito: [],
        total: 0,
        carrito_length: 0,
      }
    },
    methods: {
      logout(){
          if (this.$route.name !== 'home') {
            this.$store.dispatch('logout');
            this.$router.push({name: 'home'});
            this.carrito = [];
            this.carrito_length = 0;
          } else {
            this.$store.dispatch('logout');
            this.carrito = [];
            this.carrito_length = 0;
          }
      },
      init_carrito(){
        if (this.$store.state.token != null) {
          axios.get(this.$url+'/obtener_carrito_cliente', {
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': this.$store.state.token,
                }
            }).then((result) => {
                  this.total = 0;
                  this.carrito_length = result.data.carrito_general.length
                  for (var item of result.data.carrito_general) {
                    let subtotal = item.producto.precio * item.cantidad;
                    this.total = this.total + subtotal; 
                  }
                    this.carrito = result.data.carrito;
                }).catch((err) => {
                    console.log(err);
                });
        }
      },
      convertCurrency(number){
        return currency_formatter.format(number, { code: 'COP' });
      },  
    },
    beforeMount() {
      this.init_carrito();
    },
    created() {
      this.sockets.subscribe('listen_cart', (data) => {
        this.init_carrito();
        this.user = JSON.parse(this.$store.state.user);
    });
    },
    components: { RouterLink }
}
  </script>
  
 <style>
.navbar-light .navbar-nav .nav-link, .navbar-hover-light:hover .navbar-nav .nav-link, .navbar-fixed-light.fixed-top .navbar-nav .nav-link {
    color: rgb(255 255 255) !important;
}

</style>