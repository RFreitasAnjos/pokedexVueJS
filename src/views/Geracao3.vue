<script setup>
import { onMounted,ref } from "vue";

let carregamento = ref([])

let vetor = ref([]);

let termoFiltragem = ref('');

onMounted(async () => {
  for (let indice = 252; indice <= 386; indice++) {
    let req = await fetch("https://pokeapi.co/api/v2/pokemon/"+indice);
    let pokemon = await req.json();
    vetor.value.push(pokemon);
  }

  carregamento.value=false
});

function filtragem(){
    return vetor.value.filter(obj => obj.name.includes(termoFiltragem.value))
}

</script>
<template>

    <div class="carregamento" v-if="carregamento">
        <img src="../complements/pikachuload.gif" alt="loadpikachu">
    </div>
  <main class="container" v-if="!carregamento">

    <!-- Filtragem -->
    <div class="column">
        <div class="">
            <input class="input" v-model="termoFiltragem" type="text" placeholder="Qual Pokemon você está procurando?">

            <p v-if="filtragem().length == 0" >Não foi encontrado nenhum Pokemon.</p>
            <p v-else-if="filtragem().length == 1" >Foi encontrado apenas um Pokemon.</p>
            <p v-else>Foram encontrados {{ filtragem().length }} Pokemons.</p>
        </div>   
    </div>

    <!-- Listagem -->
    <div class="columns is-multiline">
        <div class="column is-narrow is-one-quarter" v-for="v in filtragem()">
            <div class="card">
                <img class="card-image" :class="v.types[0].type.name" :src="v.sprites.other.home.front_default" alt="pokemon">
                <p>{{ v.name }}</p>
                <p>{{ v.types[0].type.name }}</p>
            </div>
        </div>
    </div>
  </main>
</template>
