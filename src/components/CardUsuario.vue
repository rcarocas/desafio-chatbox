<template>
  <div class="cardusuario">
    <div class="card ">
      <img :src="usuario.picture.large" class="card-img-top" :alt="usuario.name.first" />
      <div class="card-body">
        <h6 class="card-title">{{ nombreCompleto }}</h6>
        <form>
          <input class="form-control my-2" type="color" name="color" id="color" v-model="mensaje.color" />
          <textarea class="form-control my-2" name="chat" id="chat" v-model="mensaje.texto" @keyup.enter="enviarMensaje"></textarea>
          <br />
          <button @click.prevent="enviarMensaje" class="btn btn-info">
            Enviar
          </button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'CardUsuario',
    props: {
        usuario: Object,
    },
    // 
    data() {
        return {
            mensaje: {
                texto: "",
                color: "#fff",
                id: "",
            }
        }
    },
    computed: {
        nombreCompleto() {
            return `${this.usuario.name.first} ${this.usuario.name.last}`
        }
    },
    methods: {
        enviarMensaje() {
            this.mensaje.id = this.usuario.id.value
            this.mensaje.nombreCompleto = this.nombreCompleto
            this.$emit("enviarMensaje", this.mensaje)
            this.mensaje.texto = "";
        }
    },
    created() {
        console.log(this.usuario);
    },
}
</script>

<style scoped></style>
