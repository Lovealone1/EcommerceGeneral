<template>
    <div >
        <section class="product-details" style="margin-top: 8rem !important;">
            <div class="container">
                <div class="row">
                <div class="col-lg-7 pt-4 order-2 order-lg-1">
                    <div class="row">   
                    <div class="d-none d-md-block col-md-2 pe-0">
                        <div class="owl-thumbs" data-slider-id="1">
                        <button class="owl-thumb-item detail-thumb-item mb-3" v-if="galeria[0]">
                            <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[0].imagen" alt="Modern Jacket 0">}
                        </button>
                        <button class="owl-thumb-item detail-thumb-item mb-3" v-if="galeria[1]">
                            <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[1].imagen" alt="Modern Jacket 0">}
                        </button>
                        <button class="owl-thumb-item detail-thumb-item mb-3" v-if="galeria[2]">
                            <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[2].imagen" alt="Modern Jacket 0">}
                        </button>
                        <button class="owl-thumb-item detail-thumb-item mb-3" v-if="galeria[3]">
                            <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[3].imagen" alt="Modern Jacket 0">}
                        </button>
                        <button class="owl-thumb-item detail-thumb-item mb-3" v-if="galeria[4]">
                            <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[4].imagen" alt="Modern Jacket 0">}
                        </button>
                        </div>
                    </div>
                    <div class="col-12 col-md-10 detail-carousel">
                        <div class="ribbon ribbon-info">Fresh</div>
                        <div class="ribbon ribbon-primary">Sale</div>
                        <div class="owl-carousel detail-slider owl-theme owl-dots-modern" data-slider-id="1">
                        <div class="item" v-if="galeria[0]">
                            <a class="glightbox" :href="$url+'/obtener_galeria_producto/'+galeria[0].imagen" data-title="Modern Jacket 1 - Caption text" data-gallery="product-gallery">
                                <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[0].imagen" alt="Modern Jacket 1">
                            </a>
                        </div>
                        <div class="item" v-if="galeria[1]">
                            <a class="glightbox" :href="$url+'/obtener_galeria_producto/'+galeria[1].imagen" data-title="Modern Jacket 1 - Caption text" data-gallery="product-gallery">
                                <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[1].imagen" alt="Modern Jacket 1">
                            </a>
                        </div>
                        <div class="item" v-if="galeria[2]">
                            <a class="glightbox" :href="$url+'/obtener_galeria_producto/'+galeria[2].imagen" data-title="Modern Jacket 1 - Caption text" data-gallery="product-gallery">
                                <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[2].imagen" alt="Modern Jacket 1">
                            </a>
                        </div>
                        <div class="item" v-if="galeria[3]">
                            <a class="glightbox" :href="$url+'/obtener_galeria_producto/'+galeria[3].imagen" data-title="Modern Jacket 1 - Caption text" data-gallery="product-gallery">
                                <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[3].imagen" alt="Modern Jacket 1">
                            </a>
                        </div>
                        <div class="item" v-if="galeria[4]">
                            <a class="glightbox" :href="$url+'/obtener_galeria_producto/'+galeria[4].imagen" data-title="Modern Jacket 1 - Caption text" data-gallery="product-gallery">
                                <img class="img-fluid" :src="$url+'/obtener_galeria_producto/'+galeria[4].imagen" alt="Modern Jacket 1">
                            </a>
                        </div>
                        </div>
                    </div>
                    </div>
                </div>
                <div class="col-lg-5 ps-lg-4 order-1 order-lg-2">
                    <ul class="breadcrumb undefined">
                    <li class="breadcrumb-item"><router-link to="/">Inicio</router-link></li>
                    <li class="breadcrumb-item"><router-link to="/shop">Tienda</router-link></li>
                    <li class="breadcrumb-item active"><router-link :to="{name: 'shop', query: {categoria: producto.categoria}}">{{producto.categoria}}</router-link></li>
                    </ul>
                    <h3 class="mb-4">{{producto.titulo}}</h3>
                    <div class="d-flex flex-column flex-sm-row align-items-sm-center justify-content-sm-between mb-4">
                    <ul class="list-inline mb-2 mb-sm-0">
                        <li class="list-inline-item h4 fw-light mb-0">{{ convertCurrency(producto.precio) }}</li>
                        <li class="list-inline-item text-muted fw-light" v-if="producto.descuento"> 
                        <del>$90.00</del>
                        </li>
                    </ul>
                    <div class="d-flex align-items-center">
                        <ul class="list-inline me-2 mb-0">  
                        <li class="list-inline-item me-0">
                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                        </li>
                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                        <li class="list-inline-item me-0"><i class="fa fa-star text-gray-300"></i></li>
                        </ul><span class="text-muted text-uppercase text-sm">25 reviews</span>
                    </div>
                    </div>
                    <p class="mb-4 text-muted">{{producto.descripcion}}</p>
                    <div class="row">
                        <div class="col-sm-6 col-lg-12 detail-option mb-3">
                        <h6 class="detail-option-heading">{{ producto.str_variedad }}</h6>
                        <label class="btn btn-sm btn-outline-secondary detail-option-btn-label" style="margin-right: 3px;" :id="'variacion_'+item._id" :for="'variacion_'+item._id" v-for="item in variaciones"
                        v-on:click="getVariacion(item._id)"> {{item.variacion}}
                            <input class="input-invisible" type="radio" name="size" :value="item._id" :id="'variacion_'+item._id" required>
                        </label>
                        </div>

                        <!-- <div class="col-12 detail-option mb-3">
                        <h6 class="detail-option-heading">Colour <span>(required)</span></h6>
                        <ul class="list-inline mb-0 colours-wrapper">
                            <li class="list-inline-item">
                            <label class="btn-colour" for="colour_Blue" style="background-color: #668cb9"> </label>
                            <input class="input-invisible" type="radio" name="colour" value="value_Blue" id="colour_Blue" required>
                            </li>
                            <li class="list-inline-item">
                            <label class="btn-colour" for="colour_White" style="background-color: #fff"> </label>
                            <input class="input-invisible" type="radio" name="colour" value="value_White" id="colour_White" required>
                            </li>
                            <li class="list-inline-item">
                            <label class="btn-colour" for="colour_Violet" style="background-color: #8b6ea4"> </label>
                            <input class="input-invisible" type="radio" name="colour" value="value_Violet" id="colour_Violet" required>
                            </li>
                            <li class="list-inline-item">
                            <label class="btn-colour" for="colour_Red" style="background-color: #dd6265"> </label>
                            <input class="input-invisible" type="radio" name="colour" value="value_Red" id="colour_Red" required>
                            </li>
                        </ul>
                        </div> -->
                        <div class="col-12 col-lg-6 detail-option mb-5">
                        <label class="detail-option-heading fw-bold">Cantidad</label>
                        <input class="form-control detail-quantity" name="items" type="number" v-model="obj_carrito.cantidad">
                        </div>
                    </div>
                    <ul class="list-inline">
                        <li class="list-inline-item">
                        <button class="btn btn-dark btn-lg mb-1" type="button" v-on:click="add_cart()">Agregar al carrito</button>
                        </li>
                        <!-- <li class="list-inline-item"><a class="btn btn-outline-secondary mb-1" href="#"> <i class="far fa-heart me-2"></i>Add to wishlist</a></li> -->
                    </ul>
                    <span class="text-danger" v-if="msm_error">{{ msm_error }}</span>
                </div>
                </div>
            </div>
            </section>
            <section class="mt-5">
            <div class="container">
                <ul class="nav nav-tabs flex-column flex-sm-row" role="tablist">
                <li class="nav-item"><a class="nav-link detail-nav-link active" data-bs-toggle="tab" href="#additional-information" role="tab">Información adicional</a></li>
                <li class="nav-item"><a class="nav-link detail-nav-link" data-bs-toggle="tab" href="#reviews" role="tab">Reviews</a></li>
                </ul>
                <div class="tab-content py-4">
                <div class="tab-pane active" id="additional-information" role="tabpanel">
                    <div class="row">
                    <div class="col-lg-6">
                        <table class="table text-sm">
                        <tbody>
                            <tr>
                            <th class="text-uppercase fw-normal">Product #</th>
                            <td class="text-muted">{{producto._id}}</td>
                            </tr>
                            <tr>
                            <th class="text-uppercase fw-normal ">Producto</th>
                            <td class="text-muted border-0" :title="producto.titulo" v-if="producto.titulo">{{producto.titulo.substr(0,20)}}</td>
                            </tr>
                            <tr>
                            <th class="text-uppercase fw-normal border-0">Fecha</th>
                            <td class="text-muted border-0">{{convertDate(producto.createdAt)}}</td>
                            </tr>
                        </tbody>
                        </table>
                    </div>
                    <div class="col-lg-6">
                        <table class="table text-sm">
                        <tbody>
                            <tr>
                            <th class="text-uppercase fw-normal ">Categoria</th>
                            <td class="text-muted ">{{producto.categoria}}</td>
                            </tr>
                            <tr>
                            <th class="text-uppercase fw-normal ">Subcategoria</th>
                            <td class="text-muted ">{{producto.subcategoria}}</td>
                            </tr>
                            <tr>
                            <th class="text-uppercase fw-normal ">Variaciones</th>
                            <td class="text-muted ">{{producto.str_variedad}}</td>
                            </tr>
                            
                            
                        </tbody>
                        </table>
                    </div>
                    </div>
                </div>
                <div class="tab-pane" id="reviews" role="tabpanel">
                    <div class="row">
                    <div class="col-lg-10 col-xl-9" v-if="reviews.length >= 1">
                        <div class="review d-flex" v-for="item in reviews">
                        
                        <div>
                            <h5 class="mt-2 mb-1">{{item.cliente.nombres}}</h5>
                            <div class="mb-2">
                                <div class="d-flex align-items-center">
                                        <ul class="list-inline me-2 mb-0" v-if="item.estrellas == 1">  
                                        <li class="list-inline-item me-0">
                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                        </li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        </ul>

                                        <ul class="list-inline me-2 mb-0" v-if="item.estrellas == 2">  
                                        <li class="list-inline-item me-0">
                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                        </li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        </ul>

                                        <ul class="list-inline me-2 mb-0" v-if="item.estrellas == 3">  
                                        <li class="list-inline-item me-0">
                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                        </li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        </ul>

                                        <ul class="list-inline me-2 mb-0" v-if="item.estrellas == 4">  
                                        <li class="list-inline-item me-0">
                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                        </li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                        </ul>

                                        <ul class="list-inline me-2 mb-0" v-if="item.estrellas == 5">  
                                        <li class="list-inline-item me-0">
                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                        </li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                        </ul>
                                    </div>
                            </div>
                            <p class="text-muted">{{ item.comentario }}</p>
                        </div>
                        </div>
                        <div class="col-lg-10 col-xl-9" v-if="reviews.length == 0">
                            <div class="row justify-content-center">
                                <div class="col-sm-8 col-md-5 text-center mb-md-0 mb-4 pb-md-0 pb-3 mx-auto">
                                <img class="mb-3 mt-5" src="/assets/media/cuaderno.gif" width="120" alt="Customer Support">
                                <h4 class=" mb-2 text-muted" style="font-weight: 400;">Producto aún sin reseñas</h4>
                                </div>
                            </div>
                        </div>
                    </div>
                    </div>
                </div>
                </div>
            </div>
            </section>
            <section class="my-5">
            <div class="container">
                <header class="text-center">
                <h6 class="text-uppercase mb-5">You might also like</h6>
                </header>
                <div class="row">
                <!-- product-->
                <div class="col-lg-2 col-md-4 col-6" v-for="item in productos_relacionados">
                    <router-link :to="{name: 'show-product', params: {slug: item.slug}}"> 
                        <div class="product">
                        <div class="product-image">
                            <div class="ribbon ribbon-danger" v-if="item.descuento">Oferta</div>
                            <img class="img-fluid" :src="$url+'/obtener_portada_producto/'+item.portada" alt="product"/>
                            <div class="product-hover-overlay">
                            <a class="product-hover-overlay-link" href="detail.html"></a>                 
                            </div>
                        </div>
                        <div class="py-2">
                            <p class="text-muted text-sm mb-1">{{item.categoria}}</p>
                            <h3 class="h6 text-uppercase mb-1" style="text-overflow: ellipsis;overflow: hidden; white-space: nowrap;" >
                            <a class="text-dark">{{item.titulo}}</a>
                            </h3>
                            <span class="text-muted">{{convertCurrency(item.precio)}}</span>
                        </div>
                        </div>
                    </router-link>
                    
                </div>
                <!-- /product-->
                </div>
            </div>
            </section>
    </div>
</template>
<script>
import { init_carrusel } from '../../../public/assets/js/theme.d7b4a888.js';
import axios from 'axios';
import currency_formatter from 'currency-formatter';
import moment from 'moment';
import $ from 'jquery';

export default {
    name: 'ShowProdcutoApp',
    data() {
        return {
            galeria : [],
            producto: {},
            variaciones: [],
            productos_relacionados: [],
            obj_carrito: {
                cantidad: 1,
            },
            user_data: JSON.parse(this.$store.state.user),
            msm_error: '',
            reviews: [],
        }
    },
    methods: {
        init_data(){
            axios.get(this.$url+'/obtener_producto_slug/'+this.$route.params.slug, {
                headers: {
                    'Content-Type': 'application/json'
            }}).then((result) => {
                this.producto = result.data.producto;
                this.obj_carrito.producto = this.producto._id;
                this.obj_carrito.cliente = this.user_data._id;

                this.galeria = result.data.galeria;
                this.variaciones = result.data.variaciones;

                this.init_productos_relacionados(this.producto.categoria);
                this.init_reviews(this.producto._id);
            }).catch((err) => {
                console.log(err);
            });
        },
        init_reviews(id){
            axios.get(this.$url+'/obtener_reviews_producto/'+id, {
                headers: {
                    'Content-Type': 'application/json'
            }}).then((result) => {
                this.reviews = result.data;
            }).catch((err) => {
                console.log(err);
            });
        },
        convertCurrency(number){
                return currency_formatter.format(number, { code: 'COP' });
        },
        convertDate(date){
            return moment(date).format('DD/MM/yyyy');
        }, 
        init_productos_relacionados(categoria){
            axios.get(this.$url+'/obtener_producto_categoria/'+categoria, {
                headers: {
                    'Content-Type': 'application/json'
            }}).then((result) => {
                this.productos_relacionados = result.data.productos;
            }).catch((err) => {
                console.log(err);
            });
        },
        getVariacion(value){
            this.obj_carrito.variacion = value;
            setTimeout(() => {
                $('.detail-option-btn-label').removeClass('bg_variedad')
                $('#variacion_'+value).addClass('bg_variedad')
            }, 50);
            console.log(this.obj_carrito);
        },
        add_cart(){
            if (!this.obj_carrito.variacion) {
                this.msm_error ='Seleccione la variacion';
            }else if(!this.obj_carrito.cantidad){
                this.msm_error ='Ingrese la cantidad';
            }else if(this.obj_carrito.cantidad <= 0){
                this.msm_error ='Ingrese una cantidad valida';
            }else{
                this.msm_error = '';
                axios.post(this.$url+'/crear_producto_carrito',this.obj_carrito, {
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': this.$store.state.token,
                }
            }).then((result) => {
                    this.$socket.emit('send_cart',true);
                }).catch((err) => {
                    console.log(err);
                });
            }
        }
    },
    beforeMount() {
        init_carrusel.init_galeria();
        this.init_data();
        init_carrusel.init_zoom();
    },
}
</script>
<style>

.detail-nav-link.nav-link.active, .detail-nav-link.nav-link:hover, .detail-nav-link.nav-link:focus {
    color: #343a40 !important;
    border-color: #fff #fff #343a40 !important;
    background: #e4e4e4 !important;
}

.product-hover-overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(255,255,255,0.92);
    opacity: 0;
    transition: opacity 0.3s;
}

.product-image{
    height: 60%;
}

.bg_variedad{
    background: #b8b8b8 !important;
    color: #000000 !important;
}
</style>