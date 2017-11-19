<template>
    <div class="col-md-12">
        <Item 
            v-for="(item, index) in items"
            :key="index"
            :passed-item="item"
            :type="type"
        />
    </div>
</template>

<script>
import Item from './Item.vue';

export default {
    data() {
        return {
            type: this.$route.params.type,
            items: []
        }
    },
    watch: {
        '$route': 'fetchItems'
    },
    methods: {
        fetchItems() {
            this.items = [];
            this.type = this.$route.params.type
            let initId = [1, 3, 9];

            for(let i in initId) {
                let id = initId[i];
                fetch(`https://swapi.co/api/${this.type}/${id}`, {
                    method: 'GET'
                })
                .then(res => res.json())
                .then(json => this.items.push(json));
            }
        }
    },
    created() {
        this.fetchItems();
    },
    components: {
        Item
    }
}
</script>