<template>
  <div class="container">
    <div class="section">
      <h1>Приложение для заметок</h1>
    </div>
    <div class="section">

      <note-form v-on:addingNote="addNote"></note-form>

    </div>
    <div class="section">
      <div class="notes-header">
        <h2>Список заметок</h2>
        <span class="notes-count">Всего заметок: {{ count }}</span>
      </div>

      <note-card v-on:removingNote="removeNote" v-for="(note, idx) of notes" :key="idx" :note="note" :idx="idx"></note-card>

    </div>
  </div>
</template>

<script>
  import NoteCard from './components/note-card.vue';
  import NoteForm from './components/note-form.vue'

  export default {
    name: 'App',

    components: {NoteCard, NoteForm},

    computed: {
      count() {
        return this.notes.length
      },
    },

    data() {
      return {
        notes: [],
      }
    },

    methods: {
      addNote(detail) {
        const createdNote = { text: detail, isEditing: false }
        this.notes.push(createdNote)
      },

      removeNote(detail) {
        this.notes.splice(detail, 1)
      },
    },
  }
</script>

<style>
  * {
    box-sizing: border-box;
  }
  body {
    font-family: Arial, sans-serif;
    background-color: #f8f8ff;
    margin: 0;
    padding: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 20px;
  }
  .container {
    max-width: 1000px;
    min-width: 300px;
    width: 100%;
    background: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  .section {
    margin-bottom: 20px;
    padding: 20px;
    background: #f4f4f9;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.05);
  }
  h1 {
    text-align: center;
    color: #333;
    margin-top: 0;
  }
  .note-form {
    display: flex;
    flex-direction: column;
  }
  .note-form textarea {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    margin-bottom: 10px;
    border-radius: 4px;
    border: 1px solid #ccc;
  }
  .note-form button {
    padding: 10px;
    font-size: 16px;
    color: #fff;
    background-color: #007bff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  .note-form button:hover {
    background-color: #0056b3;
  }
  textarea {
    resize: none;
    width: 100%;
  }
  .notes-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .notes-count {
    font-size: 16px;
    color: #555;
  }
  .notes {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 20px;
  }
  .note-card {
    background: #fff;
    padding: 15px;
    border-radius: 8px;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
    position: relative;
  }
  .note-card p {
    margin: 0;
    color: #333;
  }
  .note-card .note-content {
    margin-bottom: 10px;
  }
  .note-card .note-actions {
    text-align: right;
  }
  .note-card button {
    background-color: #ff4d4d;
    border: none;
    color: white;
    padding: 5px 10px;
    border-radius: 4px;
    cursor: pointer;
  }
  .note-card button:hover {
    background-color: #cc0000;
  }
  :focus {
    border: 5px solid red;
  }
</style>
