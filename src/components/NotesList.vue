<template>
  <div class="notes">
    <button
      class="btn btn-new-note"
      @click="saveNewNote"
    >Save Note</button>
    <div class="
      notes__items">
      <Note
        v-for="(note, index) in notes"
        :key="index"
        v-bind="note"
        class="notes__items__item"
        @select-note="selectNote($event, note)"
      ></Note>
    </div>
  </div>
</template>

<script>
import Note from './NoteItem';
export default {
  props: {
    notes: {
      type: Array
    }
  },
  components: {
    Note
  },
  methods: {
    saveNewNote () {
      this.$emit('save-note');
    },
    selectNote ($event, note) {
      this.$emit('select-note', note.body);
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../styles/components/notes-list.scss";
</style>