<template>
  <div class="notes-container">
    <NotesList
      :notes="notes"
      class="notes-container__list"
      @save-note="saveNote"
      @select-note="selectNote"
    ></NotesList>
    <NotesCreate
      :note="currentNote"
      @note-content-change="noteContentChanged"
      class="notes-container__create"
    ></NotesCreate>
  </div>
</template>

<script>
import NotesCreate from './NotesCreate';
import NotesList from './NotesList';
import axios from 'axios';

export default {
  data () {
    return {
      notes: [],
      currentNote: null
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
  },
  methods: {
    selectNote (note) {
      this.currentNote = note;
    },
    noteContentChanged (note) {
      this.currentNote = note;
    },
    saveNote () {
      const note = {
        title: this.currentNote.substring(0, 25),
        body: this.currentNote
      };

      axios.post('http://localhost:7071/api/notes-create', note).then(() => {
        this.notes.push(note);
        this.currentNote = null;
      });
    }
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