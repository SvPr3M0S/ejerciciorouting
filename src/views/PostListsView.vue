<template>
    <h1 class="post">Listado de posts <button class="btn btn-primary">Estilado con bootstrap</button></h1>
    <ul class="post-list">
         <li v-for="post in posts" :key="post.id">{{ post.title }}</li>
    </ul>
 </template>
 
 <script lang="ts" setup>
 import PostService from '@/services/PostService';
 import {onMounted } from 'vue';
 const service = new PostService()
 const posts = service.getPosts()
 
 onMounted(async () => {
     await service.fetchAll() //espera
 })
 // list-style-type: none; quita los puntos en el interface
 </script>
 
 
 <style scoped lang="scss">
    .post-list {
        width: 95vw;
        height: 75px;
        padding: 20px;
        list-style-type: none; 
        li {
        padding: 10px;
        width: 100%;
        border: 1px solid #ccc;
        color: red;
        }

        li:hover {
            background-color: darken(#000000, 10%);
        }
    }

    .post {
        color: blue;
    }

 </style>

