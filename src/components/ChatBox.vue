<template>
    <div class="container py-2 overflow-auto border rounded h-100 bg-success-subtle bg-gradient">
        <div v-for="(mensaje, index) in mensajes" :key="index" :style="{textAlign: mensaje.id === usuarios[0].id.value ? 'left' : 'right' }" class="">
            <small >{{ mensaje.nombreCompleto }}</small><br>
            <span class="border rounded p-1" :style="{ backgroundColor: mensaje.color }" > {{ mensaje.texto
                }}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ChatBox',
    props: {
        mensajes: Array,
        usuarios: Array
    }
}

</script>

<style scoped></style>