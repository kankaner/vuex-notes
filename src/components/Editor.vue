<template>
<div id="note-editor">
    <div class="form-group">
        <input type="text" name="title" class="title form-control" placeholder="请输入标题" @input="updateNote" v-model="currentNote.title">
        <textarea v-model="currentNote.content" name="content" class="form-control" row="3" placeholder="请输入正文" @input="updateNote"></textarea>
    </div>
</div>
</template>

<script>
import { mapActions,mapGetters } from 'vuex'

export default {
    computed:{
        currentNote(){
            return this.$store.getters.activeNote
        },
        ...mapGetters([
            'activeNote'
        ])
    },
    methods:{
        updateNote(){
            this.$store.commit('EDIT_NOTE',this.currentNote)
        },
        ...mapActions([
            'editNote'
        ])
    }
}
</script>
