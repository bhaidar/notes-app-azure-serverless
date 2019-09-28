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
        class="select-note"
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

<style scoped>
.notes {
  overflow: auto;
  height: 100vh;

  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

.btn {
  cursor: pointer;
  padding: 12px;
  background: #7c5cbf;
  border: none;
  color: #fff;
  font-size: 16px;
  transition: background 0.3s ease;
}

.notes__items {
  color: white;
  margin: 0 16px 16px 16px;
}

.btn-new-note {
  margin: 16px;
  align-self: center;
}

.select-note {
  cursor: pointer;
}

.select-note:hover {
  transition: background 0.3s ease;
  background: #6e7491;
}
</style>