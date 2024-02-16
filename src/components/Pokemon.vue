<template>
  <div v-if="pokeTp" class="MyFlexItem">
    <h4>{{ pokeTp.name }}</h4>
    <img :src="pokeTp.sprites.front_default" alt="">
    <div v-for="(stat, index) in pokeTp.stats" class="statsFlex" :key="index">
      <span>
        {{ stat.stat.name }}:
      </span>
      <span>
        {{ stat.base_stat }}
      </span>
    </div>
    <div class="typesFlex">
      <span v-for="(type, index) in pokeTp.types" class="tipos" :class="type.type.name" :key="index">
        {{ type.type.name }}
      </span>
    </div>
  </div>
</template>

<script setup lang="ts">
import axios from 'axios';
import { onMounted, ref } from 'vue';

const pokeTp = ref();

const {url} = defineProps({
  url: String
});

onMounted(async()=>{
  const response = await axios.get(url!);
  pokeTp.value = response.data;
})

</script>

<style lang="scss" scoped>
h4{
  margin: 3px;
  text-transform: uppercase;
}
.MyFlexItem{
  padding: 5px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.typesFlex{
  margin: 5px 10px;
  display: flex;
  width: 100%;
  justify-content: space-around;
}
.statsFlex{
  margin: 2px 10px;
  padding: 0px 20px;
  display: flex;
  width: 100%;
  justify-content: space-between;
}


.tipos{
  padding: 5px;
  border-radius: 15px;
  border: 3px double;
  text-transform: capitalize;
}

.normal {
  background: #A8A77A;
  border-radius: 15px;
}

.fire {
  background: #EE8130;
  border-radius: 15px;
}

.water {
  background: #6390F0;
  border-radius: 15px;
}

.electric {
  background: #F7D02C;
  border-radius: 15px;
}

.grass {
  background: #7AC74C;
  border-radius: 15px;
}

.ice {
  background: #96D9D6;
  border-radius: 15px;
}

.fighting {
  background: #C22E28;
  border-radius: 15px;
}

.poison {
  background: #A33EA1;
  border-radius: 15px;
}

.ground {
  background: #E2BF65;
  border-radius: 15px;
}

.flying {
  background: #A98FF3;
  border-radius: 15px;
}

.psychic {
  background: #F95587;
  border-radius: 15px;
}

.bug {
  background: #A6B91A;
  border-radius: 15px;
}

.rock {
  background: #B6A136;
  border-radius: 15px;
}

.ghost {
  background: #735797;
  border-radius: 15px;
}

.dragon {
  background: #6F35FC;
  border-radius: 15px;
}

.dark {
  background: #705746;
  border-radius: 15px;
}

.steel {
  background: #B7B7CE;
  border-radius: 15px;
}

.fairy {
  background: #D685AD;
  border-radius: 15px;
}
</style>