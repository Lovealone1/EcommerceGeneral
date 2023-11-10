<template>
    <div style="background: #f5f5f5;" class="pb-5">
        <section class="hero" style="margin-top: 7rem !important;">
            <div class="container">
                <!-- Breadcrumbs -->
                <ol class="breadcrumb justify-content-center">
                <li class="breadcrumb-item"><router-link to="/">Home</router-link ></li>
                <li class="breadcrumb-item active">Direcciones</li>
                </ol>
                <!-- Hero Content-->
                <div class="hero-content pb-5 text-center">
                <h1 class="hero-heading">Direcciones</h1>
                </div>
            </div>
            </section>
            <section>
            <div class="container">
                <div class="row mb-5">
                <div class="col-lg-8 col-xl-9">
                    <div class="block">
                        <!-- Invoice Address-->
                        <div class="block-header" style="background: #005f96;">
                        <h6 class="text-uppercase mb-0 text-white">Nueva Direccion</h6>
                        </div>
                        <div class="block-body">
                        <div class="row">
                            <div class="form-group col-md-6">
                            <label class="form-label" for="fullname_invoice"><b>Nombres</b></label>
                            <input class="form-control" type="text" placeholder="Nombres" v-model="direccion.nombres">
                            </div>
                            <div class="form-group col-md-6">
                            <label class="form-label" for="phonenumber_invoice"><b>Apellidos</b></label>
                            <input class="form-control" type="text" placeholder="Apellidos" v-model="direccion.apellidos">
                            </div>
                            <div class="form-group col-md-6">
                            <label class="form-label" for="emailaddress_invoice"><b>Correo electrónico</b></label>
                            <input class="form-control" type="text" placeholder="test@gmail.com" v-model="direccion.email">
                            </div>
                            <div class="form-group col-md-6">
                            <label class="form-label" for="street_invoice"><b>Documento</b></label>
                            <input class="form-control" type="text" placeholder="123456789" v-model="direccion.documento">
                            </div>
                            <div class="form-group col-md-6">
                            <label class="form-label" for="street_invoice"><b>Dirección</b></label>
                            <input class="form-control" type="text" placeholder="Cll KR #00-00" v-model="direccion.direccion">
                            </div>
                            <div class="form-group col-md-6">
                            <label class="form-label" for="city_invoice"><b>Estado / Municipio</b></label>
                            <select class="form-control" v-model="direccion.estado">
                                <option value="" disabled selected>Seleccionar...</option>
                                <option :value="item" v-for="item in $estados">{{ item }}</option>
                            </select>
                            </div>
                            <div class="form-group col-md-6">
                            <label class="form-label" for="zip_invoice"><b>Detalle de la dirección</b></label>
                            <input class="form-control" type="text" placeholder="Apartamento - Casa" v-model="direccion.detalle_direccion">
                            </div>
                            <div class="form-group col-md-6">
                            <label class="form-label" for="zip_invoice"><b>Código postal</b></label>
                            <input class="form-control" type="text" placeholder="Código postal" v-model="direccion.zip">
                            </div>
                            <div class="form-group col-md-6">
                            <label class="form-label" for="state_invoice"><b>Ciudad</b></label>
                            <input class="form-control" type="text" placeholder="Ciudad" v-model="direccion.ciudad">
                            </div>
                            <div class="form-group col-md-6">
                            <label class="form-label" for="phonenumber_invoice"><b>Telefono</b></label>
                            <input class="form-control" type="text" placeholder="+57 300 000 00 00" v-model="direccion.telefono">
                            </div>
                        </div>
                        <!-- /Invoice Address-->
                        </div>
                    </div>
                    <div class="mb-4 mt-3 text-center">
                        <button class="btn btn-dark" type="button" v-on:click="crear_direccion()">Crear dirección <img src="/assets/media/ubicacion-del-mapa.png" style="width: 18px;"></button>
                    </div>

                    <div class="text-center" v-if="msm_error">
                        <span class="text-danger">{{msm_error}}</span>
                    </div>

                    <table v-if="direcciones.length >= 1" class="table table-bordered table-striped" style="margin-top: 3rem !important;background: white !important;">
                    <thead class="table-dark" >
                        <tr>
                        <th scope="col">Destinatario</th>
                        <th scope="col">Contacto</th>
                        <th scope="col">Localización</th>
                        <th scope="col">Dirección</th>
                        <th scope="col">Opciones</th>
                        </tr>
                    </thead>
                    <tbody C>
                        <tr v-for="item in direcciones">
                            <th scope="row">
                                <small>{{ item.nombres }} {{ item.apellidos }}</small><br>
                                <small>{{ item.documento }}</small>
                            </th>
                            <td>
                                <small>{{ item.email }}</small><br>
                                <small>{{ item.telefono }}</small>
                            </td>
                            <td>
                                <small>{{ item.estado }} {{ item.ciudad }}</small><br>
                                <small> {{ item.zip }}</small>
                            </td>
                            <td>
                                <small>{{ item.direccion }}</small><br>
                                <small v-if="item.detalle_direccion">{{ item.detalle_direccion }}</small>
                            </td>
                            <td>
                                <div class="text-center">
                                    <a class="cart-remove" style="cursor: pointer;" v-on:click="eliminar_direccion(item._id)">
                                    <img src="/assets/media/compartimiento.png">
                                    </a>
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>
                <div class="card" v-if="direcciones.length == 0">
                    <div class="card-body">
                        <div class="row" >
                            <div class="col-12 text-center">
                                <img src="/assets/media/camion-de-reparto.gif" style="width: 90px;">
                                <h4 style="color: rgb(167, 167, 167); margin-top: 5px;">No hay direcciones para mostrar.</h4>
                                <span class="text-muted">Ingresa una dirección.</span>
                            </div>
                    </div>
                    </div>
                </div>
                </div>
                
                <!-- Customer Sidebar-->
                <div class="col-xl-3 col-lg-4 mb-5">
                    <SidebarCliente /> 
                </div>
                    
                </div>
            </div>
            </section>
    </div>
</template>

<script>
import axios from 'axios';
import SidebarCliente from '@/components/SidebarCliente.vue';
    export default {
        data() {
            return {
                direccion: {
                    estado: '',
                },
                direcciones: [],
                msm_error: ''
            }
        },
        methods: {
            crear_direccion(){
                if (!this.direccion.nombres) {
                    this.msm_error = 'Ingrese su nombre'
                }else if(!this.direccion.apellidos) {
                    this.msm_error = 'Ingrese sus apellidos'
                }else if(!this.direccion.email) {
                    this.msm_error = 'Ingrese su correo electrónico'
                }else if(!this.direccion.documento) {
                    this.msm_error = 'Ingrese su documento'
                }else if(!this.direccion.direccion) {
                    this.msm_error = 'Ingrese su dirección'
                }else if(!this.direccion.estado) {
                    this.msm_error = 'Seleccione su municipio'
                }else if(!this.direccion.zip) {
                    this.msm_error = 'Ingrese su código postal'
                }else if(!this.direccion.ciudad) {
                    this.msm_error = 'Ingrese su ciudad'
                }else if(!this.direccion.telefono) {
                    this.msm_error = 'Ingrese su teléfono'
                }else{
                    
                    axios.post(this.$url+'/crear_direccion_cliente', this.direccion, {
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token,
                    }
                    }).then((result) => {
                        this.msm_error = '';
                        this.direccion = {
                            estado: '',
                        }
                        this.init_direcciones();
                    }).catch((err) => {
                        console.log(err);
                    });
                }
            },
            init_direcciones(){
                axios.get(this.$url+'/obtener_direcciones_cliente', {
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token,
                    }
                    }).then((result) => {
                        this.direcciones = result.data;
                    }).catch((err) => {
                        console.log(err);
                    });
            },
            eliminar_direccion(id){
                axios.delete(this.$url+'/eliminar_direcciones_cliente/'+id, {
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token,
                    }
                    }).then((result) => {
                        this.init_direcciones();
                    }).catch((err) => {
                        console.log(err);
                    });
            }
        },
        components: {
            SidebarCliente
        },
        beforeMount() {
            this.init_direcciones();
        },
    }
</script>

<style>

</style>