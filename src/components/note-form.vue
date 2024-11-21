<template>
  <div class="note-form">
    <textarea
      ref="mainTextarea"
      v-model.trim="message"
      id="note-content"
      rows="4"
      placeholder="Введите вашу заметку..."
    ></textarea>
    <button v-on:click="$emit('addingMessage', message), this.message = ''" id="add-note">Добавить заметку</button>
  </div>
</template>

<script>
  export default {
    emits: ['addingMessage'],

    data() {
      return {
        message: ''
      }
    },

    methods: {

    }
  }
</script>