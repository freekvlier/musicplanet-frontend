<template>
    <Navbar />

      <!-- Center -->
    <div class="flex flex-row flex-grow text-xl h-screen pb-14">
        <NavbarLeft :refreshPlaylistsTrigger="trigger"/>
        
        <!-- Main Content -->
        <div class="flex-grow p-10">
        <a class="flex flex-grow font-bold text-3xl border-b-2 p-2 border-gray-600">{{this.$route.name}}</a>

        <!-- Begin Content -->
        <transition name="fade">
            <router-view @refreshPlaylists="trigger = !trigger"/>
        </transition>
        <!-- End Content -->
        
        </div>
    </div>
</template>

<script>
import Navbar from '../components/Admin/Navigation/Navbar.vue'
import NavbarLeft from '../components/Admin/Navigation/NavbarLeft.vue'
import axios from 'axios';
import http from "../http-common";

export default {
    components: {Navbar, NavbarLeft},
     data(){
      return{
        trigger: false
      }
    },
    methods: {
    }
}
</script>

<style>
.fade-enter-active, .fade-leave-active {
    transition: opacity .2s
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
    opacity: 0
}   
</style>