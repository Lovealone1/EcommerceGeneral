<template>
    <div style="margin-top: 9rem !important;">
        <section class="hero" v-if="estado == 'pending '|| estado == 'failure' ">
            <div class="container">
                <!-- Breadcrumbs -->
                <ol class="breadcrumb justify-content-center">
                    <li class="breadcrumb-item"><router-link to="/">Inicio</router-link ></li>
                <li class="breadcrumb-item active">Frequently asked questions        </li>
                </ol>
                <!-- Hero Content-->
                <div class="hero-content pb-5 text-center">
                <h1 class="mb-5">No se pudo completar el pago</h1>
                <div class="row">   
                    <div class="col-xl-8 offset-xl-2"><p class="lead mb-0">As am hastily invited settled at limited civilly fortune me. Really spring in extent an by. Judge but built party world. Of so am he remember although required. Bachelor unpacked be advanced at. Confined in declared marianne is vicinity. </p></div>
                </div>
                </div>
            </div>
        </section>
        <section class="hero" v-if="estado == 'success'" style="margin-top: 9rem !important;">
            <div class="container" v-if="!msm_error"> 
                <!-- Breadcrumbs -->
                <ol class="breadcrumb justify-content-center">
                    <li class="breadcrumb-item"><router-link to="/">Inicio</router-link ></li>
                <li class="breadcrumb-item active">Frequently asked questions        </li>
                </ol>
                <!-- Hero Content-->
                <div class="hero-content pb-5 text-center">
                <h1 class="mb-5">Validando pago...</h1>
                <div class="row">   
                    <div class="col-xl-8 offset-xl-2"><img src="/assets/media/ahorrar-dinero.gif" style="width: 120px;"></div>
                </div>
                </div>
            </div>
            <div class="container" v-if="msm_error"> 
                <!-- Breadcrumbs -->
                <ol class="breadcrumb justify-content-center">
                    <li class="breadcrumb-item"><router-link to="/">Inicio</router-link ></li>
                <li class="breadcrumb-item active">Frequently asked questions        </li>
                </ol>
                <!-- Hero Content-->
                <div class="hero-content pb-5 text-center">
                <h1 class="mb-5">{{msm_error}}</h1>
                <div class="row">   
                    <div class="col-xl-8 offset-xl-2"><p class="lead mb-0">Su pago no fue aprobado, por favor intentelo de nuevo </p></div>
                </div>
                </div>
            </div>
        </section>
    </div>
    
</template>

<script>
import axios from 'axios';
    export default {
        name: 'VerificacionView',
        data() {
            return {
                estado: '',
                payment_id: '',
                pago: {},
                direccion: '',
                msm_error: '',
                venta: {},
                detalles: [],
                total: 0,
                carrito: [],
            }
        },
        beforeMount() {
            let user_data = JSON.parse(this.$store.state.user);
            this.estado = this.$route.params.estado;
            this.payment_id = this.$route.query.payment_id;
            this.init_payment(this.payment_id);
            this.init_carrito();
            this.venta.envio = this.$envio;
            this.venta.cliente = user_data._id;
            this.venta.transaccion = this.payment_id;

            console.log(this.$route.params);
            if (this.$route.params.direccion) {
                this.direccion = this.$route.params.direccion;
                this.venta.direccion = this.direccion;
            }else{
                this.msm_error = 'No se encontró una dirección'
            }

            console.log(this.detalles);
        },
        methods: {
            init_payment(payment_id){
                axios.get('https://api.mercadopago.com/v1/payments/'+payment_id,{
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': 'Bearer TEST-4643553258623544-111100-d5f2e2590c5b28a698510bb951b12b66-583533437' ,
                    }
                }).then((result) => {
                    this.pago = result.data;
                    if (this.pago.status == 'approved') {
                        this.validar_venta(this.payment_id)                        
                    }else{
                        this.msm_error = 'El pago no fue aprobado'
                    }
                }).catch((err) => {
                    console.log(err);
                });
            },
            validar_venta(payment_id){
                axios.get(this.$url+'/validar_payment_id_venta/'+payment_id,{
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token,
                    }
                }).then((result) => {
                    if (result.data.length>=1 ) {
                        this.msm_error = 'El pago ya está asignado a una venta'
                    }else if(result.data.length == 0){
                        this.crear_venta();
                    }
                }).catch((err) => {
                    console.log(err);
                });
            },
            init_carrito(){
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
                        this.detalles.push({
                            subtotal: subtotal,
                            precio_unidad: item.producto.precio,
                            cantidad: item.cantidad, 
                            cliente: this.venta.cliente,
                            producto: item.producto._id,
                            variacion: item.variacion._id,
                        })
                    }
                    this.carrito = result.data.carrito_general;
                    this.venta.total = this.total;
                }).catch((err) => {
                        console.log(err);
                });
            },
            crear_venta(){
                this.venta.detalles = this.detalles
                axios.post(this.$url+'/crear_venta_cliente',this.venta,{
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token,
                    }
                }).then((result) => {
                    //redirect
                    this.$socket.emit('send_cart',true);
                }).catch((err) => {
                    console.log(err);
                });
            }
        },
    }
</script>

<style >

</style>