<template>
  <div id="app" class="modal-fullscreen" :class="{ 'show': this.show }">
    <div class="modal-content">
      <div class="modal-header">
        <slot name="header"></slot>
      </div>
      <div class="modal-body" :class="{ 'modal-scrollable': scrollable }">
        <slot name="body"></slot>
      </div>
      <div class="footer">
        <slot name="footer"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'modal-fullscreen-vue',

  props: {
    show: { type: Boolean, required: true },
    scrollable: { type: Boolean, default: true }
  },

  watch: {
    show (show) {
      this.$emit('show', show)
    }
  }
}
</script>

<style scoped>
  .modal-fullscreen {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    opacity: 0;
    visibility: hidden;
    transform: scale(1.1);
    transition: visibility 0s linear 0.25s, opacity 0.25s 0s, transform 0.25s;
  }

  .modal-fullscreen .modal-content {
    position: absolute;
    top: 50%;
    left: 50%;
    width: 100%;
    height: 100%;
    transform: translate(-50%, -50%);
    background-color: white;
    padding: 1rem 1.5rem;
    border-radius: 0.5rem;
  }

  .modal-fullscreen .modal-header {
    padding: 21.2px 0px;
  }

  .modal-fullscreen .modal-body {
    height: calc(100vh - 130px);
    max-height: inherit;
  }

  .modal-fullscreen .modal-body {
    height: calc(100vh - 130px);
    max-height: inherit;
  }

  .show {
    opacity: 1;
    visibility: visible;
    transform: scale(1.0);
    transition: visibility 0s linear 0s, opacity 0.25s 0s, transform 0.25s;
  }

  .modal-scrollable {
    overflow-y: auto;
  }
</style>
