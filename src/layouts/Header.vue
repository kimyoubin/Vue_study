<template>
    <header>
        <div class="wrap">
            <router-link 
                v-for="(item, key) in route"
                :key="key"
                :to="item.path"
                :class="{ 'on' : item.path === $route.path }"
                @click="$emit('click', key)">{{ item.menu }}</router-link>
            <!-- <router-link to="/about">ABOUT</router-link>
            <router-link to="/list">LIST</router-link> -->
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            route: [
                {
                    menu: 'HOME',
                    path: '/'
                },
                {
                    menu: 'ABOUT',
                    path: '/about'
                },
                {
                    menu: 'LIST',
                    path: '/list'
                },
            ]
        }
    }
}
</script>

<style lang="scss" scope>
header {
    background: #fff;
    .wrap {
        width: 720px;
        margin: 0 auto;
        display: flex;
        justify-content: center;
        align-items: center;
        a {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 150px;
            height: 100px;
            font-size: 17px;
            font-weight: bold;
            &.on {
                color: red;
            }
        }
    }
}
</style>