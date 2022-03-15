<template>
  <transition name="modal-animation">
  <div v-show="modalActive" class="modal">
      <transition name="modal-animation-inner">
      <div v-show="modalActive" class="modal-inner">
          <i class="far fa-times-circle"></i>
          <!-- modal-content -->
          <slot/>
          <button>Close</button>
      </div>
      </transition>
  </div>
  </transition>
</template>

<script>
export default {
props: ["modalActive"]
}
</script>

<style>

</style>