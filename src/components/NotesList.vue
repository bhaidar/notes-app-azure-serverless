<template>
  <div class="notes">
    <button class="btn btn-new-note">Save Note</button>
    <div class="notes__items">
      <Note
        v-for="(note, index) in notes"
        :key="index"
        v-bind="note"
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
</style>