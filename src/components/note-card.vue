<template>
  <div class="note-card">
    <div class="note-content">
      <textarea
        ref="editingTextarea"
        v-if="note.isEditing"
        v-model="note.text"
        v-on:blur="saveNote(idx)"
        v-on:keyup.enter="saveNote(idx)"
        type="text"
      ></textarea>
      <p v-else v-on:dblclick="EditNote(idx)">{{ note.text }}</p>
    </div>
    <div class="note-actions">
      <button v-on:click="handleClickButtonRemove(idx)">Удалить</button>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['note', 'idx'],
    emits: ['removingNote'],
    emits: ['savingNoteText'],

    data() {
      return {
        isEditing: false,
        editedText: this.note.text,
      }
    },

    methods: {
      handleClickButtonRemove(idx) {
        this.$emit('removingNote', idx)
      },

      editNoteText(idx) {
        // this.notes[idx].isEditing = true
        // this.$nextTick(() => {
        //   this.$refs.editingTextarea[0].focus()
        // })
        this.editedText = this.note.text
        this.$emit('savingNoteText', { idx: this.idx, text: this.editedText })
        this.note.isEditing = true
      },

      saveNote(idx) {
        // this.$emit('savingNoteText', { idx: this.idx, text: this.editedText })
        // this.notes[idx].isEditing = false
      },
    },
  }
</script>
