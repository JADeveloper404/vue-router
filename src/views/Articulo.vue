<template>
  <Titulo :texto="post.id + ' - ' + post.title" />
  <p>{{ post.body }}</p>
</template>

<script>
import Titulo from '@/components/Titulo'

export default {
    components: {
        Titulo
    },
    data() {
        return {
            post: {}
        }
    },
    methods: {
        async obtenerArticulo(id) {
            const data = await fetch('https://jsonplaceholder.typicode.com/posts/' + id)
            const obj = await data.json();
            this.post = obj;
        }
    },
    created() {
        this.obtenerArticulo(this.$route.params.id);
    }
}
</script>

<style>

</style>