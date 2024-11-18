<template>
  <div id="app">
    <main class="my-5 container">
            <div class="row">
                <div class="col-3 ">
                    <CardUsuario :usuario="usuarios[0]"
                        @enviarMensaje="enviarMensajeHandler" 
                        />
                </div>
                <div class="col-6 ">
                  <ChatBox :mensajes="mensajes" :usuarios="usuarios" />
                </div>
                <div class="col-3 ">
                    <CardUsuario :usuario="usuarios[1]"
                        @enviarMensaje="enviarMensajeHandler" 
                        />
                </div>
            </div>
        </main>
  </div>
</template>

<script>
import axios from "axios";
import CardUsuario from "./components/CardUsuario.vue";
import ChatBox from "./components/ChatBox.vue";

export default {
  name: "App",
  components: {
    CardUsuario,
    ChatBox,
  },
  data() {
        return {
            usuarios: [],
            mensajes: [],
        }
    },
  methods: {
    async getUsuario() {
      try {
        let response = await axios.get("https://randomuser.me/api/?results=2");
        this.usuarios = response.data.results;
      } catch (error) {
        console.log(error);
      }
    },
    enviarMensajeHandler(mensaje) {
            let nuevoMensaje = {
                id: mensaje.id,
                color: mensaje.color,
                nombreCompleto: mensaje.nombreCompleto,
                texto: mensaje.texto,

            }
            this.mensajes.push(nuevoMensaje)
        }
    
  },
  mounted() {
    this.getUsuario();
  },
};
</script>

<style>

</style>
