<template>
  <div class="note-card">
    <div class="note-content">
      <textarea
        v-if="note.isEditing"
        v-model="note.text"
        v-on:blur="note.isEditing = false"
        ref="elTextarea"

      ></textarea>
      <p v-else v-on:dblclick="editNoteText">{{ note.text }}</p>
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

    methods: {
      handleClickButtonRemove(idx) {
        this.$emit('removingNote', idx)
      },

      editNoteText(idx) {
        this.note.isEditing = true
        this.$nextTick(() => {
          console.log(this.$refs.elTextarea)
          this.$refs.elTextarea.focus()
        })
      },
    },
  }
</script>
