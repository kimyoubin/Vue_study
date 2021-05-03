<template>
  <vue-layout>
    <div class="wrap">
      Home
    </div>
  </vue-layout>
</template>

<script>
import VueLayout from '@/layouts/index.vue'

export default {
  name: 'Home',
  components: { VueLayout },
}
</script>

<style lang="scss" scoped>
.wrap {
  max-width: 720px;
  margin: 0 auto;
  padding: 70px 0;
}

</style>