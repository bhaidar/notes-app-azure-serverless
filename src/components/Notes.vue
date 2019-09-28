<template>
  <div class="notes-container">
    <NotesList
      :notes="notes"
      class="notes-container__list"
    ></NotesList>
    <NotesCreate class="notes-container__create"></NotesCreate>
  </div>
</template>

<script>
import NotesCreate from './NotesCreate';
import NotesList from './NotesList';
import axios from 'axios';

export default {
  data () {
    return {
      notes: []
    }
  },
  components: {
    NotesCreate,
    NotesList
  },
  mounted () {
    axios.get('http://localhost:7071/api/notes-read-all')
      .then(response => {
        this.notes = response.data.map(note => note.data);
      });
  }
}
</script>

<style scoped>
.notes-container {
  display: flex;
  justify-content: space-between;
}

.notes-container__list {
  width: 250px;
  background: #333744;
  flex-shrink: 0;
}

.notes-container__create {
  flex-grow: 1;
  display: flex;
}
</style>