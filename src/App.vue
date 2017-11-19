<template>
    <div id="app">
        <h1>
            {{ title }}
        </h1>
        <h3>
            <router-link class="link" to="/data/people">Meet the People</router-link> |
            <router-link class="link" to="/data/planets">See All Planets</router-link>
        </h3>
        <router-view></router-view>
    </div>
</template>

<script>
export default {
    name: 'app',
    data() {
        return {
            title: 'Generate Your Team',
        };
    }
}
</script>
