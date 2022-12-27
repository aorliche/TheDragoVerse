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
        <img :src="focused.img">
        <div class="ability">
            <h3>Ability: <span class="heading">{{ focused.ability.name }}</span></h3>
            <div class="tagline">{{ focused.ability.tagline }}</div>
            <div class="desc">{{ focused.ability.desc }}</div>
        </div>
    </div>
    <div v-else>Scroll over or click a class</div>
</template>

<style scoped>
.details {
    position: relative;
    text-align: left;
}
.tagline {
    font-style: italic;
}
.ability, img {
    margin-top: 0.5rem;
}
.name, .heading {
    color: var(--color-heading);
}
img {
    height: 16rem;
}
</style>