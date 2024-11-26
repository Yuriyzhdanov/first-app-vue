<template>
  <div class="note-form">
    <textarea
      ref="mainTextarea"
      v-model.trim="noteText"
      id="note-content"
      rows="4"
      placeholder="Введите вашу заметку..."
    ></textarea>
    <button v-on:click="handleClickButton" id="add-note">
      Добавить заметку
    </button>
  </div>
</template>

<script>
  export default {
    emits: ['addingNote'],

    data() {
      return {
        noteText: '',
      }
    },

    methods: {
      handleClickButton() {
        this.$emit('addingNote', this.noteText)
        this.noteText = ''
      },
    },
  }
</script>
