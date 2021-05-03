<template>
    <div>
        <vue-header></vue-header>
        <slot></slot>
        <vue-footer></vue-footer>
    </div>
</template>

<script>
import VueHeader from "@/layouts/Header.vue";
import VueFooter from "@/layouts/Footer.vue";

export default {
    name: 'Index',
    components: {VueHeader, VueFooter},    
}
</script>

<style>

</style>