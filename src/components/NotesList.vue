<template>
<div id="notes-list">
    <div id="list-header">
        <h2>Notes | heavenru.com</h2>
        <div class="btn-group btn-group-justified" role="group">
            <!-- all -->
            <div class="btn-group" role="group">
                <button type="button" class="btn btn-default" @click="toggleShow('all')" :class="{active: show === 'all'}">All Notes</button>
            </div>

            <!-- favorites -->
            <div class="btn-group" role="group">
                <button type="button" class="btn btn-default" @click="toggleShow('favorite')" :class="{active: show === 'favorite'}">Favorites</button>
            </div>
        </div>
    </div>

    <!-- 渲染笔记列表 -->
    <div class="container">
        <div class="list-group">
            <a v-for="note in filteredNotes" class="list-group-item" href="#" :class="{active: activeNote === note}" @click="updateActiveNote(note)">
                <h4 class="list-group-item-heading">
            {{note.title.trim().substring(0,30)}}
          </h4>
            </a>
        </div>
    </div>
</div>
</template>

<script>
import { mapActions,mapGetters } from 'vuex'

export default {
    computed:mapGetters([
        'show',
        'activeNote',
        'filteredNotes'
    ]),
    methods:{
        toggleShow(show){
            this.$store.dispatch('updateShow',show)
        },
        ...mapActions([
            'updateActiveNote',
            'updateShow'
        ])
    }
}
</script>
