<script setup lang="js">
const props = defineProps({
  monster: { type: Object, required: true },
});
</script>
<template>
  <div
    class="bg-teal-800 rounded-lg shadow-xs border m-2 p-6 max-w-sm min-w-sm flex flex-col text-center align-center"
  >
    <h2 class="mb-2 text-2xl">{{ monster.name }}</h2>
    <img class="border rounded-2xl max-h-60" :src="'https://www.dnd5eapi.co' + monster.image" :alt="monster.name + ' Image'">
    <p>Hit Points: {{ monster.hit_points }}</p>
    <p>Size: {{ monster.size }}</p>
    <p>Type: {{ monster.type }}</p>
    <p>Alignment: {{ monster.alignment }}</p>
    <p>
      <ul>
        Stats
        <li class="list-none">Strength: {{ monster.strength }}</li>
        <li class="list-none">Dexterity: {{ monster.dexterity }}</li>
        <li class="list-none">Constitution: {{ monster.constitution }}</li>
        <li class="list-none">Intelligence: {{ monster.intelligence }}</li>
        <li class="list-none">Wisdom: {{ monster.wisdom }}</li>
        <li class="list-none">Charisma: {{ monster.charisma }}</li>
      </ul>
    </p>
    <ul>
      Speed:
      <li v-for="(move, key) in monster.speed" class="list-none">{{ key }}: {{ move }}</li>
    </ul>
    <ul>
      Senses:
      <li v-for="(sense, key) in monster.senses" class="list-none">{{ key.replaceAll("_", " ") }}: {{ sense }}</li>
    </ul>
  </div>
</template>
