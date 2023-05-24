<template>
    <div class="card">
        <div class="card-body">
            <input type="text" class="form-control form-control-lg" placeholder="Ingrese numero de orden de compra" v-model="ordenDeCompra">
            <button class="btn agregar-orden" @click="enviarData">Agregar nueva compra</button>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import axios from 'axios';
import swal from 'sweetalert';

const ordenDeCompra = ref('');
const url = 'https://test.iaudisis.com/audisis/AppNat_Pedidos/guardar_pedido';

const enviarData = () => {
    const options = {
        method: 'POST',
        url: 'https://test.iaudisis.com/audisis/AppNat_Pedidos/guardar_pedido',
        data: {
            IdUsuario: 75282,
            AccessToken: 'e6ef992a745855ecb1accf7a20b491a76d3089baa4aca3b54269a83f1fdfeb4a6c639c93d33fc179eb23216638ad8046fdb88e950f209d20015b4622b4115b82',
            Negocio: 'Agrocommerce',
            RutCliente: '00760766305',
            CodigoLocal: '00760766305DEFAULT',
            Fecha: '2023-03-21 11:21:28',
            FormaPago: 'CONTADO',
            IdUsuarioCliente: 'AUDPRUEBAS',
            OrdenDeCompra: ordenDeCompra.value,
            Comentario: 'Ninguno ',
            CantidadProductos: 11,
            IdLocal: 11087,
            TieneCambioDePrecio: false,
            TotalPedido: 0,
            NombreCliente: null,
            TelefonoCliente: null,
            DireccionDespacho: null,
            FechaRegistro: null,
            IdEncabezado: 0,
            Bodega: null,
            Region: null,
            Comuna: null,
            Estado: 0,
            AprobacionAdicional: 0,
            Productos: [
                {
                    Codigo: '808743603631',
                    Descripcion: 'Aceite 100% Maravilla Bonanza 12x900 cc',
                    Precio: 22320,
                    CantidadPedido: 1,
                    Linea: 1,
                    FechaPrometidaEntrega: '26-03-2023',
                    PesosAgregados: 0,
                    TipoCambio: 'Ninguno',
                    Bodega: 'CDACSA'
                },
                {
                    Codigo: '073116400006',
                    Descripcion: 'Alimento Vegetal Violife Bloque Sabor Gouda 13x200 Gr',
                    Precio: 25896,
                    CantidadPedido: 1,
                    Linea: 2,
                    FechaPrometidaEntrega: '26-03-2023',
                    PesosAgregados: 0,
                    TipoCambio: 'Ninguno',
                    Bodega: 'CDACSA'
                },
                {
                    Codigo: '073116400010',
                    Descripcion: 'Alimento Vegetal Violife Granulado Sabor Mozarella 4x2.5 Kg',
                    Precio: 68100,
                    CantidadPedido: 1,
                    Linea: 3,
                    FechaPrometidaEntrega: '26-03-2023',
                    PesosAgregados: 0,
                    TipoCambio: 'Ninguno',
                    Bodega: 'CDACSA'
                }
            ]
        }
    };

    axios.request(options).then(function (response) {
        swal("Orden ingresada!", ordenDeCompra.value , "success");
    }).catch(function (error) {
        console.error(error.response.data.mensaje);
        if (error.response.data.mensaje === 'Ya existe un pedido con el mismo código de compra.') {
            swal("Orden de compra ya existe!", ordenDeCompra.value , "error");
        } else if (error.response.data.mensaje === 'La información enviada no es válida'){
            swal("Error al ingresar orden, información no válida!", ordenDeCompra.value , "error");
        } else {
            console.log(error)
            swal("Error desconocido!", ordenDeCompra.value , "error");
        }
    });
}

</script>

<style scoped>
.card {
    margin-top: 20px;
    margin-bottom: 20px;
    width: 50%;
}

.agregar-orden {
    margin-top: 20px;
    margin-bottom: 20px;
    background-color: rgba(28, 14, 118, 0.7);
    color: white;
}

.agregar-orden:hover {
    background-color: rgba(28, 14, 118, 1);
    color: white;
}
</style>