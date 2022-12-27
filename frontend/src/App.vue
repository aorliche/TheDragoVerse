<script setup>
// import HelloWorld from "./components/HelloWorld.vue";
// import TheWelcome from "./components/TheWelcome.vue";
import PigClass from "./assets/images/main/PigClass.png";
import ChickenClass from "./assets/images/main/ChickenClass.png";
import KomodoClass from "./assets/images/main/KomodoClass.png";
import FoxRogue from "./assets/images/main/FoxRogue.png";
import SpiderWizard from "./assets/images/main/SpiderWizard.png";
import SpiderFighter from "./assets/images/main/SpiderFighter.png";
import ClassDetailsVue from "./components/ClassDetails.vue";
import { ref, reactive } from 'vue';

class Stats {
  constructor(str, spd, sns, mojo) {
    this.str = str;
    this.spd = spd;
    this.sns = sns;
    this.mojo = mojo;
  }

  toString() {
    return  `Strength: ${this.str}, Speed: ${this.spd}, Sense: ${this.sns}, Mojo: ${this.mojo}`;
  }
}

class Ability {
  constructor(name, tagline, desc) {
    this.name = name;
    this.tagline = tagline;
    this.desc = desc;
  }
}

function alt(blk) {
  return blk.name.replace(' ', '');
}

const PigClassBlock = {
  img: PigClass,
  name: "Pig Class",
  tagline: "Sturdy warrior with a snout for loot",
  stats: new Stats(4,2,1,1),
  ability: new Ability("Root", "Get in there, piggy", "Discover nearby loot and turn enemy corpses into money, mana, and quintessence"),
}

const ChickenClassBlock = {
  img: ChickenClass,
  name: "Chicken Class",
  tagline: "Feathery medic with a surprising amount of agility",
  stats: new Stats(2,4,1,2),
  ability: new Ability("Roost", "Golden-colored egg", "Take a short amount of time to convert mana into healing or buffs for teammates")
}

const KomodoClassBlock = {
  img: KomodoClass,
  name: "Komodo Class",
  tagline: "A land-based dragon with a keen mind and high magic",
  stats: new Stats(1,1,4,3),
  ability: new Ability("Parthenogenesis", "They're never alone", "Use a lot of mana to spawn a new basic teammate")
}

const FoxRogueBlock = {
  img: FoxRogue,
  name: "Fox Rogue",
  tagline: "An unaligned canid whose intentions are often mercurial",
  stats: new Stats("?", "?", "?", "?"),
  ability: new Ability("Hydrophobia", "One bite", "Unknown")
}

const SpiderWizardBlock = {
  img: SpiderWizard,
  name: "Spider Wizard",
  tagline: "A spinner of threads and deceptions, high in magic",
  stats: new Stats("?", "?", "?", "?"),
  ability: new Ability("Threads", "The world wide web", "Unknown")
}

const SpiderFighterBlock = {
  img: SpiderFighter,
  name: "Spider Fighter",
  tagline: "A poisonous hunter who eschews traps for raw power",
  stats: new Stats("?", "?", "?", "?"),
  ability: new Ability("Arthromegaly", "Large and in charge", "Unknown")
}

const classes = [PigClassBlock, ChickenClassBlock, KomodoClassBlock];
const unaligned = [FoxRogueBlock];
const enemies = [SpiderWizardBlock, SpiderFighterBlock];

const focused = ref(null);

function focus(blk) {
  // alert(blk.stats.str)
  focused.value = blk;
}
</script>

<template>
  <header>
    <h1 class="banner">
      Welcome to the DragoVerse!
    </h1>
    <div class="tagline">
      A fantasy world of cooperating, persistent AI agents
    </div>
    <ClassDetailsVue :focused="focused"></ClassDetailsVue>
  </header>

  <main>
    <h2>Choose your class</h2>
    <div>
      You will have multiple agents working for you, but you start with just one
    </div>
    <div class="images">
      <img class='critter' @mouseover="focus(blk)" v-for="blk in classes" :src="blk.img" :alt="alt(blk)">
    </div>
    <h2>Meet the unaligned</h2>
    <div>
      Some AIs are not managed by any players, but have their own goals
    </div>
    <div class="images">
      <img class='critter' @mouseover="focus(blk)" v-for="blk in unaligned" :src="blk.img" :alt="alt(blk)">
    </div>
    <h2>Defend the DragoVerse</h2>
    <div>
      Many AIs are beholden to the enemy, who seeks to destroy all non-machine interlopers
    </div>
    <div class="images">
      <img class='critter' @mouseover="focus(blk)" v-for="blk in enemies" :src="blk.img" :alt="alt(blk)">
    </div>
  </main>
</template>

<style scoped>
header {
  text-align: center;
}
.images img {
  height: 8rem;
  box-sizing: content-box;
  border: 0.2rem solid var(--color-border);
  margin-right: 0.5rem;
}
.tagline {
  margin-bottom: 2rem;
}
.critter:hover {
  border: 0.2rem solid var(--color-border-hover);
}
img[alt=PigClass] {
  background: linear-gradient(0deg, #fac4b1, #c9a568);
}
img[alt=ChickenClass] {
  background: linear-gradient(0deg, #81c995, #bceec9);
}
img[alt=KomodoClass] {
  background: linear-gradient(0deg, #fbd7d4, #f28b82);
}
img[alt=FoxRogue] {
  background: linear-gradient(0deg, #fdd663, #fbeab9);
}
img[alt=SpiderWizard] {
  background: linear-gradient(0deg, #8ab4f8, #c58af9);
}
img[alt=SpiderFighter] {
  background: linear-gradient(0deg, #c58af9, #8ab4f8);
}
</style>
