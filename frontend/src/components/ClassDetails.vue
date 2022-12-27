<script setup>
defineProps({
  focused: {
    type: Object,
  },
});
</script>

<template>
    <div v-if="focused" class="details">
        <h2 class="name">{{ focused.name }}</h2>
        <div class="tagline">{{ focused.tagline }}</div>
        <div class="stats">{{ focused.stats }}</div>
        <div class="ability">
            <h3>Ability: {{ focused.ability.name }}</h3>
            <div class="tagline">{{ focused.ability.tagline }}</div>
            <div class="desc">{{ focused.ability.desc }}</div>
        </div>
    </div>
    <div v-else>No details here</div>
</template>

<style scoped>
.details {
    position: relative;
    text-align: left;
}
.tagline {
    font-style: italic;
}
.ability {
    margin-top: 1rem;
}
</style>