<template>
    <div style="background: #ebebeb;" class="pb-5">
        <section class="hero" style="margin-top: 6.5rem !important;">
      <div class="container" >
        <!-- Breadcrumbs -->
        <ol class="breadcrumb justify-content-center">
          <li class="breadcrumb-item"><router-link to="/">Inicio</router-link ></li>
          <li class="breadcrumb-item active">Orders        </li>
        </ol>
        <!-- Hero Content-->
        <div class="hero-content pb-5 text-center">
          <h1 class="hero-heading">Tus Compras</h1>
          <div class="row">   
            <div class="col-xl-8 offset-xl-2"><p class="lead">Aquí tienes tu historial de compras</p></div>
          </div>
        </div>
      </div>
    </section>
    <section>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-xl-9">
            <table class="table table-borderless table-hover table-responsive-md" >
              <thead class="text-white" style="background: #2c2c2c;">
                <tr>
                  <th class="py-4 text-uppercase text-sm">Order #</th>
                  <th class="py-4 text-uppercase text-sm">Date</th>
                  <th class="py-4 text-uppercase text-sm">Total</th>
                  <th class="py-4 text-uppercase text-sm">Status</th>
                  <th class="py-4 text-uppercase text-sm">Action</th>
                </tr>
              </thead>
              <tbody style="background: white;">
                <tr v-for="item in ventas">
                  <th class="py-4 align-middle"># {{ item.serie.toString().padStart(4,'0000') }}</th>
                  <td class="py-4 align-middle">{{convertDate(item.createdAt)}}</td>
                  <td class="py-4 align-middle">{{convertCurrency(item.total+item.envio)}}</td>
                  <td class="py-4 align-middle"><span class="badge p-2 text-uppercase badge-success-light">{{item.estado}}</span></td>
                  <td class="py-4 align-middle"><router-link class="btn btn-outline-dark btn-sm" :to="{name: 'venta', params: {id:item._id}}">Detalles</router-link></td>
                </tr>
              </tbody>
            </table>
          </div>
          <div class="col-xl-3 col-lg-4 mb-5">
                    <SidebarCliente /> 
                </div>
        </div>
      </div>
    </section>
    </div>
</template>

<script>
import SidebarCliente from '@/components/SidebarCliente.vue';
import axios from 'axios';
import moment from 'moment';
import currency_formatter from 'currency-formatter';
    export default {
        data() {
            return {
                ventas: [],
            }
        },
        components: {
            SidebarCliente
        },
        methods: {
            init_ventas(){
                axios.get(this.$url+'/obtener_ventas_cliente',{
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': this.$store.state.token
                    }
                }).then((result)=>{
                    console.log(result);
                    this.ventas = result.data;
                });
            },
            convertDate(item){
                return moment(item).format('DD/MM/yyyy')
            },
            convertCurrency(number){
                return currency_formatter.format(number, { code: 'COP' });
            },
        },
        beforeMount() {
            this.init_ventas();
        },
        name: 'HisorialComprasApp'
    }
</script>

<style>

</style>