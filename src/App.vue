<template>
<div id="app" class="app">
    <toolbar></toolbar>
    <notes-list></notes-list>
    <editor></editor>
</div>
</template>

<style>
html,
#app {
    height: 100%;
}

body {
    margin: 0;
    padding: 0;
    border: 0;
    height: 100%;
    max-height: 100%;
    position: relative;
}
</style>

<script>
import Toolbar from './components/Toolbar.vue';
import NotesList from './components/NotesList.vue';
import Editor from './components/Editor.vue';
import store from './vuex/store.js';
import { mapActions } from 'vuex'

export default {
    components: {
        Toolbar,
        NotesList,
        Editor
    },
    store,
    methods:mapActions([
        'initStore'
    ]),
    created:function () {
        this.initStore()
    }
}
</script>
