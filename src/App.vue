<template>
    <div id="app">
        <h1>
            {{ title }}
        </h1>
        <div class="col-md-12">
            <Character
                v-for="(id, index) in idTeams"
                :key="index"
                :id="id"
            />
        </div>
    </div>
</template>

<script>
import Character from './components/Character.vue';

    export default {
        name: 'app',
        data() {
            return {
                title: 'Generate Your Team',
                idTeams: [
                    1, 2, 3
                ]
            };
        },
        components: {
            Character
        }
    }
</script>
