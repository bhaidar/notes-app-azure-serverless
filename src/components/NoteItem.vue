<template>
  <div
    class="notes__item"
    @click.prevent="selectNote"
  >
    <h4>{{ title }}</h4>
    <p class="notes__item__body">{{ body }}</p>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String
    },
    body: {
      type: String
    }
  },
  methods: {
    selectNote () {
      this.$emit('select-note', this.body);
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../styles/components/note-item.scss";
</style>