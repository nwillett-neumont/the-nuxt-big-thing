<script setup>
let usedIndices = [];
let monsterIds = [];

const baseUrl = "https://www.dnd5eapi.co/api/";
await $fetch(`${baseUrl}monsters`).then((data) => {
  let random = Math.floor(Math.random() * data.count);
  for (let i = 0; i < 5; i++) {
    usedIndices.push(random);
    monsterIds.push(`${baseUrl}monsters/` + data.results[random].index);
    while (usedIndices.includes(random)) {
      random = Math.floor(Math.random() * data.count);
    }
  }
});

let monsters = ref([]);

for (let id of monsterIds) {
  let data = await $fetch(id);
  monsters.value.push(data);
}
</script>
<template>
  <div
    class="text-white flex flex-wrap justify-center"
    v-if="monsters.length === 5"
  >
    <MonsterCard
      v-for="monster of monsters"
      :key="monster.index"
      :monster="monster"
    ></MonsterCard>
  </div>
</template>
