<template>
    <div class="col-md-4" @click="switchChracter">
        <div class="character-card">
            <div class="card-block">
                <h4 class="card-title">{{ character.name }} <small>({{ character.gender }})</small></h4>
                <p class="card-text">Height: {{ character.height }}</p>
                <p class="card-text">Mass: {{ character.mass }}</p>
                <p class="card-text">Hair Color: {{ character.hair_color }}</p>
                <p class="card-text">Eye Color: {{ character.eye_color }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: [
            'id'
        ],
        data() {
            return {
                character: ''
            };
        },
        methods: {
            fetchCharacter(id) {
                fetch(`https://swapi.co/api/people/${id}`, {
                    method: 'GET'
                })
                .then(response => response.json())
                .then(json => this.character = json);
            },
            switchChracter() {
                let randomIdChar = Math.floor(Math.random() * 83) + 1;
                this.fetchCharacter(randomIdChar);
            }
        },
        created() {
            this.fetchCharacter(this.id);
        }
    }
</script>
