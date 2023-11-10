<template>
    <div style="background: #f5f5f5;" class="pb-5">
        <section class="hero" style="margin-top: 7rem !important;">
            <div class="container">
                <!-- Breadcrumbs -->
                <ol class="breadcrumb justify-content-center">
                <li class="breadcrumb-item"> <router-link to="/">Inicio</router-link> </li>
                <li class="breadcrumb-item active">Carrito</li>
                </ol>
                <!-- Hero Content-->
                <div class="hero-content pb-5 text-center">
                <h1 class="hero-heading">Carrito de compras</h1>
                <div class="row">   
                    <div class="col-xl-8 offset-xl-2"><p class="lead text-muted">¡Aquí están todos los productos que seleccionaste!</p></div>
                </div>
                </div>
            </div>
            </section>
            <!-- Shopping Cart Section-->
            <section>
            <div class="container">
                <div class="row mb-5"> 
                <div class="col-lg-8">
                    <div class="cart">
                    <div class="cart-wrapper">
                        <div class="cart-header text-center" style="background: #005f96;">
                        <div class="row">
                            <div class="col-5 text-white">Producto</div>
                            <div class="col-2 text-white">Precio</div>
                            <div class="col-2 text-white">Cantidad</div>
                            <div class="col-2 text-white">Total</div>
                            <div class="col-1 text-white"></div>
                        </div>
                        </div>
                        <div class="card-body" style="background: white;" v-if="load_data">
                            <div class="row">
                                <div class="col-12 text-center">
                                    <img src="/assets/media/caja.gif" style="width: 60px;">
                                </div>
                            </div>
                        </div>
                        <div class="cart-body" style="background: white;" v-if="!load_data">
                        <!-- Product-->
                            <div class="cart-item" v-for="item in carrito">
                            <div class="row d-flex align-items-center text-center">
                            <div class="col-5">
                                <div class="d-flex align-items-center"><a href="detail.html"><img class="cart-item-img" :src="$url+'/obtener_portada_producto/'+item.producto.portada" alt="..."></a>
                                <div class="cart-title text-start"><a class="text-uppercase text-dark" href="detail.html"><strong>{{item.producto.titulo}}</strong></a><br><span class="text-muted text-sm">{{item.producto.str_variedad}}</span><br><span class="text-muted text-sm">{{item.variacion.variacion}}</span>
                                </div>
                                </div>
                            </div>
                            <div class="col-2">{{convertCurrency(item.producto.precio)}}</div>
                            <div class="col-2">{{ item.cantidad }}</div>
                            <div class="col-2 text-center">{{ convertCurrency(item.producto.precio * item.cantidad) }}</div>
                            <div class="col-1 text-center"><a class="cart-remove" style="cursor: pointer;" v-on:click="eliminar(item._id)">
                                <img src="/assets/media/compartimiento.png">
                            </a>
                            </div>
                            </div>
                            </div>
                        </div>
                    </div>
                    </div>
                    <div class="my-5 d-flex justify-content-between flex-column flex-lg-row">
                        <router-link class="btn btn-link text-muted" to="/shop">Continuar comprando</router-link>
                        <a class="btn btn-dark">Proceed to checkout</a>
                    </div>
                </div>
                <div class="col-lg-4">
                    <div class="block mb-5">
                    <div class="block-header">
                        <h6 class="text-uppercase mb-0">Detalle de la orden</h6>
                    </div>
                    <div class="block-body bg-light pt-1">
                        <p class="text-sm">Los costos de envio se calcularán automaticamente dada la cantidad de producos ordenados</p>
                        <ul class="order-summary mb-0 list-unstyled">
                        <li class="order-summary-item"><span>Order Subtotal </span><span>{{convertCurrency(total)}}</span></li>
                        <li class="order-summary-item"><span>Costo de envío</span><span>{{convertCurrency($envio)}}</span></li>
                        <li class="order-summary-item border-0"><span>Total</span><strong class="order-summary-total" v-if="total+$envio >= 200000">{{convertCurrency(total+$envio)}}</strong></li>
                        </ul>
                    </div>
                    </div>
                </div>
                </div>
            </div>
            </section>
    </div>
</template>

<script>
import axios from 'axios';
import currency_formatter from 'currency-formatter';
    export default {
        data() {
            return {
                total: 0,
                carrito: [],
                load_data: true,
            }
        },
        methods: {
        init_carrito(){
                if (this.$store.state.token != null) {
                    this.load_data = true;
                axios.get(this.$url+'/obtener_carrito_cliente', {
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token,
                    }
                }).then((result) => {
                this.total = 0;
                for (var item of result.data.carrito_general) {
                    let subtotal = item.producto.precio * item.cantidad;
                    this.total = this.total + subtotal; 
                }
                    this.carrito = result.data.carrito_general;
                    this.load_data = false;
                }).catch((err) => {
                    console.log(err);
                });
            }
        },
        convertCurrency(number){
            return currency_formatter.format(number, { code: 'COP' });
        },
        eliminar(id){
            axios.delete(this.$url+'/eliminar_producto_carrito/'+id, {
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token,
                    }
                }).then((result) => {
                    this.init_carrito();
                    this.$socket.emit('send_cart',true);
                }).catch((err) => {
                    console.log(err);
                });
        }
    },
    beforeMount() {
        this.init_carrito();
    },
}
</script>

<style>

</style>