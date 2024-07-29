<template>
    <h1>Listado de posts <button class="btn btn-primary">Estilado con bootstrap</button></h1>
    <ul class="post-list">
        <li v-for="post in posts" :key="post.id">
            {{ post.title }}
        </li>
    </ul>
</template>

<script lang="js">

    import PostService from '@/services/PostService';
    import { defineComponent, onMounted } from 'vue';

    export default defineComponent({
        name:'PostList',
        setup(){

            const service = new PostService();
            const posts = service.getPosts();

            onMounted(async () => {
                await service.fetchAll();
            })

            return {posts}
        }
    });

</script>

<style scoped lang="scss">

*{
    margin: 0px;
    padding: 0px;
}

h1{
    text-align: center;
}

.post-list{
    width: 95vw;
    height: 75px;
    padding: 20px;
    list-style: none;

    li{
        padding: 10px;
        width: 100%;
        border: 1px solid $red;
    }

    li:hover{
        background-color: darken(black, 10%);
        color: white;
    }
}

</style>