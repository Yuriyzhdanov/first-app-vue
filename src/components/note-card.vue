<template>
    <div class="note-card">
        <div class="note-content">
            <textarea
                ref="editingTextarea"
                v-if="note.isEditing"
                v-model="note.text"
                v-on:blur="saveMessage(idx)"
                v-on:keyup.enter="saveMessage(idx)"
                type="text"
            ></textarea>
            <p v-else v-on:dblclick="editMessage(idx)">{{ note.text }}</p>
            </div>
            <div class="note-actions">
            <button v-on:click="removeMessage(idx)">Удалить</button>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['note', 'idx'],
        methods: {
            editMessage(idx) {
                this.notes[idx].isEditing = true
                this.$nextTick(() => {
                this.$refs.editingTextarea[0].focus()
                })
            },

            saveMessage(idx) {
                this.notes[idx].isEditing = false
            },
        }
    }
</script>
