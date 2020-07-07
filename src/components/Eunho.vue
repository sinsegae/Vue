<template>
    <v-container>
        <v-layout row wrap>
            <v-flex xs12>
                <Board/>
            </v-flex>
        </v-layout>
    </v-container>
</template>

<script>
import Board from './components/Board.vue'

export default {
    components: {
        Board
    }    
}
</script>