<template>
<div>
    <app-header></app-header>
    <div class="container">
        <transition  enter-active-class="animate__animated animate__lightSpeedInRight"
                    leave-active-class="animate__animated animate__lightSpeedOutLeft"
                    mode="out-in">
          <router-view></router-view>
        </transition>
    </div>
</div>
</template>

<script>
  import Header from './components/Header.vue'

  export default {
    components: {
      appHeader: Header
    }, 
    created() {
      this.$store.dispatch('initStocks');
    }
  }
</script>

<style >
:root {
  --animate-duration: 300ms;
  --animate-delay: 0.3s;
}
</style>