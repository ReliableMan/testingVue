<template>
  <div class="modal" v-if="show" @click.stop="hideModal">
    <div @click.stop class="modal_content">
      <slot></slot>
    </div>
  </div>

</template>

<script>
export default {
  name: "my-modal",
  props: {
    show: {
      type: Boolean,
      default: false
    }
  }, 
  methods: {
    hideModal() {
      this.$emit('update:show', false)
    }
  }
}
</script>

<style scoped>
.modal{
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  background: rgba(0,0,0, 0,5);
  position: fixed;
  display: flex
}

.modal_content{
  margin: auto;
  background: rgba(0, 128, 128, 0.651);
  border-radius: 15px;
  min-height: 60px;
  min-width: 400px;
  padding: 20px
}
</style>
