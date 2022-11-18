<script setup>
import { onBeforeMount,ref } from 'vue'
import axios from 'axios'

const API_ALL_AMIIBO = 'https://www.amiiboapi.com/api/amiibo/'

const amiibos = ref([])
const isDataLoading = ref(true)

onBeforeMount(async ()=>{
    const allAmiibo = await axios.get(API_ALL_AMIIBO)
    const {data,status} = allAmiibo // object destructuring FTW!
    if(status===200){
        isDataLoading.value=false
    }
    amiibos.value = data.amiibo
    console.log(data.amiibo)
})
</script>

<template>
				<section id="main">
					<div class="container">

						<!-- Content -->
							<article class="box post">
								
								<header>
									<h2>Ma Collection</h2>
									<p>(ici le nombre d'amiibo)</p>
								</header>
								<p>
									<table>
										<tr>
										  <th>Character</th>
										  <th>game Series</th>
										  <th>Action</th>
										</tr>
										<tr v-for="amiibo in amiibos" :key="amiibo.id">
										  <td>{{amiibo.character}}</td>
										  <td>{{amiibo.gameSeries}}</td>
										  <td><RouterLink :to="{name:'amiiboDetails',params:{amiiboId:amiibo.tail}}">voir</RouterLink></td>
										</tr>
									</table>
								</p>
								
							</article>

					</div>
				</section>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
