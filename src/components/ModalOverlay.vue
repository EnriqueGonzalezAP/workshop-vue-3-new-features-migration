<template>
  <button class="button" @click="openModal">Open</button>
  <teleport to="body">
    <transition>
      <div v-if="this.opened" class="background" @click="closeModal">
        <div class="modal" @click="stopPropagation">
          <div class="modal-body">
            <slot></slot>
          </div>
          <div class="modal-footer">
            <button class="button" @click="closeModal">Close</button>
          </div>
        </div>
      </div>
    </transition>
  </teleport>
</template>

<script>
export default {
  data() {
    return {
      opened: false
    }
  },
  methods: {
    openModal() {
      this.opened = true
    },
    closeModal() {
      this.opened = false
    },
    stopPropagation(e) {
        e.stopPropagation();
    }
  }
}
</script>.

<style scoped>
  .background {
    top: 0;
    position: absolute;
    height: 100vh;
    width: 100%;
    background: #000000ee;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .modal {
    display: flex;
    width: 500px;
    height: fit-content;
    flex-direction: column;
    background: white;
    color: black;
    border-radius: 8px;
  }
  .modal-body {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15px;
  }
  .modal-footer {
    margin-top: 5px;
    border-top: 1px solid black;
    padding: 15px;
  }
  .button {
    background: blue;
    color: white;
    padding: 10px 20px;
    border-radius: 8px;
  }

  /* we will explain what these classes do next! */
  .v-enter-active,
  .v-leave-active {
    transition: opacity 0.5s ease;
  }

  .v-enter-from,
  .v-leave-to {
    opacity: 0;
  }
</style>
