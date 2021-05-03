<template>
  <transition name="modal" appear>
    <div 
      @click.self="$emit('close')"
      class="modal">
      <div class="modal-box">
        <button
          @click="$emit('close')">닫기</button>
        <slot></slot>
      </div>
    </div>
  </transition> 
</template>

<script>
export default {
  name: 'Modal',  
  props: {    
    items: {
      type: Array
    },
    modalShow: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {

    }
  },
  methods: {

  }
}
</script>

<style lang="scss">
.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0,0,0,.6);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 100;
  .modal-box {
    position: relative;    
    padding: 50px 30px 30px;
    background-color: #fff;
    button {
      position: absolute;
      top: 20px;
      right: 20px;
      width: 18px;
      height: 18px;
      background: url('~@/assets/images/close_btn.png') no-repeat;
      background-size: 100%;
      font-size: 0;
    }
  }
}

.modal-enter-active, .modal-leave-active {
  transition: opacity 0.3s;

  .modal-box {
    transition: opacity 0.3s, transform 0.3s;
  }
}

.modal-leave-active {
  transition: opacity 0.3s ease;
}

.modal-enter, .modal-leave-to {
  opacity: 0;

  .modal-box {
    opacity: 0;
    transform: translateY(-10px);
  }
}
</style>
