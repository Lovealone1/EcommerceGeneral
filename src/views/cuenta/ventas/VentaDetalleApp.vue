<template>
    <div style="background: #ffffff;" class="pb-5"> 
        <div v-if="!load_data">
            <div v-if="!acceso">    
                <section class="hero" style="background: #f5f5f5;">
                    <div class="container" style="margin-top background: #f5f5f5;: 6.5rem !important;" >
                        <!-- Breadcrumbs -->
                        <ol class="breadcrumb justify-content-center">
                        <li class="breadcrumb-item"><router-link to="/">Inicio</router-link ></li>
                        </ol>
                        <!-- Hero Content-->
                        <div class="hero-content pb-5 text-center">
                        <h1 class="mb-5">No tienes acceso al historial de compras</h1>
                        <div class="row">   
                            <div class="col-xl-8 offset-xl-2"><p class="lead mb-0">Regresa a la tienda para comprar un producto</p></div>
                        </div>
                        </div>
                    </div>
                </section>
            </div>
            <div v-if="acceso">
                <section class="hero" style="margin-top: 7rem !important;">
            <div class="container">
                <!-- Breadcrumbs -->
                <ol class="breadcrumb justify-content-center">
                    <li class="breadcrumb-item"><router-link to="/">Inicio</router-link ></li>
                    <li class="breadcrumb-item"><router-link to="/">Mis compras</router-link ></li>
                <li class="breadcrumb-item active">Order #{{venta.serie.toString().padStart(4,'00')}}</li>
                </ol>
                <!-- Hero Content-->
                <div class="hero-content pb-5 text-center">
                <h1 class="hero-heading">Order #{{venta.serie.toString().padStart(4,'00')}}</h1>
                <div class="row">   
                    <div class="col-xl-8 offset-xl-2"><p class="lead text-muted">Order #{{venta.serie.toString().padStart(4,'00')}} fue hecha el <strong>{{convertDate(venta.createdAt)}}</strong> y actualmente <strong>está siendo preparada</strong>.</p><p class="text-muted">Si tienes alguna duda con tu pedido no tengas duda en <a href="contact.html">contactarnos</a>, uno de nuestros asesores te atenderá lo más rápido posible</p></div>
                </div>
                </div>
            </div>
                </section>
                <section>
            <div class="container">
                <div class="row">
                <div class="col-lg-8 col-xl-9">
                    <div class="cart">
                    <div class="cart-wrapper">
                        <div class="cart-header text-center text-white" style="background: #2c2c2c !important;">
                        <div class="row">
                        <div class="col-6">
                            <span class="text-left">Producto</span>
                        </div>
                        <div class="col-2">Precio</div>
                        <div class="col-2">Cantidad</div>
                        <div class="col-2">Total</div>
                        </div>
                    </div>
                        <div class="cart-body">
                        <!-- Product-->
                            <div v-for="item in detalles">
                                <div class="cart-item" >
                                <div class="row d-flex align-items-center text-center">
                                <div class="col-6">
                                    <div class="d-flex align-items-center">
                                        <router-link :to="{name: 'show-product', params:{slug:item.detalle.producto.slug}}">
                                        <img class="cart-item-img" :src="$url+'/obtener_portada_producto/'+item.detalle.producto.portada" alt="..."></router-link>
                                    <div class="cart-title text-start">
                                        <router-link class="text-uppercase text-dark" :to="{name: 'show-product', params:{slug: item.detalle.producto.slug}}">
                                            <strong>{{item.detalle.producto.titulo.substr(0,20)}}</strong></router-link>
                                            <br>
                                            <span class="text-muted text-sm">{{item.detalle.producto.str_variedad}}</span><br><span class="text-muted text-sm">{{item.detalle.variacion.variacion}}</span>
                                    </div>
                                    </div>
                                </div>
                                <div class="col-2">{{convertCurrency(item.detalle.producto.precio)}}</div>
                                <div class="col-2">{{ item.detalle.cantidad }}</div>
                                <div class="col-2 text-center">{{ convertCurrency(item.detalle.producto.precio * item.detalle.cantidad) }}</div>
                                
                                
                                </div>
                                </div>
                                <div class="cart-item" >
                                    <div class="row" v-if="item.reviews.length >= 1">
                                        <div class="col-12">
                                            <div class="review d-flex" style="padding-bottom: 0px !important; padding-top: 0px !important;">
                                                <div>
                                                    <div class="d-flex align-items-center">
                                                        <ul class="list-inline me-2 mb-0" v-if="item.reviews[0].estrellas == 1">  
                                                        <li class="list-inline-item me-0">
                                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                                        </li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        </ul>

                                                        <ul class="list-inline me-2 mb-0" v-if="item.reviews[0].estrellas == 2">  
                                                        <li class="list-inline-item me-0">
                                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                                        </li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        </ul>

                                                        <ul class="list-inline me-2 mb-0" v-if="item.reviews[0].estrellas == 3">  
                                                        <li class="list-inline-item me-0">
                                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                                        </li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        </ul>

                                                        <ul class="list-inline me-2 mb-0" v-if="item.reviews[0].estrellas == 4">  
                                                        <li class="list-inline-item me-0">
                                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                                        </li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella.png" style="width: 15px;"></li>
                                                        </ul>

                                                        <ul class="list-inline me-2 mb-0" v-if="item.reviews[0].estrellas == 5">  
                                                        <li class="list-inline-item me-0">
                                                            <img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;">
                                                        </li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        <li class="list-inline-item me-0"><img src="/assets/icons/silueta-de-estrella-negra.png" style="width: 15px;"></li>
                                                        </ul>
                                                    </div>
                                                <p class="text-muted"> {{ item.reviews[0].comentario }}</p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="row" v-if="item.reviews.length == 0">
                                        <div class="col-12 mb-4">
                                            <h5>Deja un comentario acerca del prodcuto</h5>
                                        </div>
                                        <div class="col-4">
                                            <star-rating :star-size="30" :animate="true" v-model="review.estrellas"></star-rating>
                                        </div>
                                        <div class="col-8 d-flex">
                                            <input type="text" class="form-control" placeholder="Deja tu comentario..." v-model="review.comentario">
                                            <button class="btn btn-primary btn-sm" style="background: #2c2c2c;" v-on:click="enviar_review(item.detalle.producto._id)">Enviar</button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    </div>
                    <div class="row my-5">
                    <div class="col-md-6">
                        <div class="block mb-5">
                        <div class="block-header">
                            <h6 class="text-uppercase mb-0">Detalles de la orden</h6>
                        </div>
                        <div class="block-body bg-light pt-1">
                            <p class="text-sm">Shipping and additional costs are calculated based on values you have entered.</p>
                            <ul class="order-summary mb-0 list-unstyled">
                            <li class="order-summary-item"><span>Subtotal </span><span>{{convertCurrency(venta.total)}}</span></li>
                            <li class="order-summary-item"><span>Precio del envío</span><span>{{convertCurrency(venta.envio)}}</span></li>
                            <li class="order-summary-item border-0"><span>Total</span><strong class="order-summary-total">{{convertCurrency(venta.total+venta.envio)}}</strong></li>
                            </ul>
                        </div>
                        </div>
                    </div>
                    <div class="col-md-6">
                        <div class="block-header">
                        <h6 class="text-uppercase mb-0">Dirección de facturación</h6> 
                        </div>
                        <div class="block-body bg-light pt-1">
                        <p>{{venta.direccion.nombres}} {{venta.direccion.apellidos}}<br>{{venta.cliente.email}}<br>{{venta.direccion.telefono}}<br>{{venta.direccion.zip}} {{venta.direccion.estado}}<br>{{venta.direccion.ciudad}}<br>{{venta.direccion.direccion}}</p>
                        </div>
                        <div class="block-header">
                        <h6 class="text-uppercase mb-0">Dirección de envío</h6>
                        </div>
                        <div class="block-body bg-light pt-1">
                        <p>{{venta.direccion.nombres}} {{venta.direccion.apellidos}}<br>{{venta.direccion.documento}}<br>{{venta.direccion.telefono}}<br>{{venta.direccion.zip}} {{venta.direccion.estado}}<br>{{venta.direccion.ciudad}}<br>{{venta.direccion.direccion}}</p>
                        </div>
                    </div>
                    </div>
                </div>
                <!-- Customer Sidebar-->
                <div class="col-xl-3 col-lg-4 mb-5">
                    <SidebarCliente /> 
                </div>
                <!-- /Customer Sidebar-->
                </div>
            </div>
                </section>
            </div>
        </div>
        <div>
            <div v-if="load_data" style="margin-top: 10rem !important;">
                    <div class="card-body">
                        <div class="row" >
                            <div class="col-12 text-center">
                                <img src="/assets/media/vacio.png" style="width: 90px;">
                                <h4 style="color: rgb(167, 167, 167); margin-top: 5px;">No hay compras que mostrar.</h4>
                                <span class="text-muted">Realiza una compra para obtener un historial que mostrar</span>
                            </div>
                    </div>
                    </div>
            </div>
        </div>
    </div>
</template>

<script>
import SidebarCliente from '@/components/SidebarCliente.vue';
import axios from 'axios';
import moment from 'moment';
import currency_formatter from 'currency-formatter';
import StarRating from 'vue-star-rating'
    export default {
        data() {
            return {
                venta: {},
                detalles: [],
                acceso: false,
                load_data: true,
                review: {},
                msm_error: '',
            }
        },
        components: {
            SidebarCliente,
            StarRating
            
        },
        name: 'VentaDetalleApp',
        beforeMount() {
            this.init_venta();
        },
        methods: {
            init_venta(){
                this.load_data = true;
                axios.get(this.$url+'/obtener_informacion_venta/'+this.$route.params.id,{
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token
                    }
                }).then((result)=>{
                    if(result.data.message){
                    this.acceso = false;
                    }else{
                    this.venta = result.data.venta;
                    this.detalles = result.data.detalles;
                    this.acceso = true;
                    }
                    this.load_data = false;
                });
            },
            convertDate(item){
                return moment(item).format('DD/MM/yyyy')
            },
            convertCurrency(number){
                return currency_formatter.format(number, { code: 'COP' });
            },
            enviar_review(id){
                if(!this.review.comentario){
                    this.msm_error = 'Ingrese un comentario'
                }else{
                    this.review.producto = id;
                    axios.post(this.$url+'/registrar_review_cliente',this.review,{
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token
                    }
                }).then((result)=>{
                    console.log(result);

                });
                }
            }
        },
    }
</script>

<style>

</style>