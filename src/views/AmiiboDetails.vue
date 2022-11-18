
<script setup>
import { useRoute } from 'vue-router';
import { onBeforeMount,ref } from 'vue'
import axios from 'axios'

const API_AMIIBO = 'https://www.amiiboapi.com/api/amiibo'

const route = useRoute()
const currentAmiibo = ref({})

onBeforeMount(async ()=>{

    const oneAmiibos = await axios.get(API_AMIIBO+'/?tail='+route.params.amiiboId)
	currentAmiibo.value = oneAmiibos.data.amiibo[0]
	console.log(oneAmiibos.data.amiibo)
})


console.log(route.params.amiiboId)

</script>

<template>
				<section id="main">
					<div class="container">
						<div class="row">
							<div class="col-4 col-12-medium">

								<!-- Sidebar -->
									<section class="box">
										<header>
											<h3>Infos</h3>
										</header>
										<p> amiiboSeries: <b>{{currentAmiibo.amiiboSeries}}</b> <br />
											character: {{currentAmiibo.character}}<br />
											gameSeries: {{currentAmiibo.gameSeries}} <br />
											type: {{currentAmiibo.type}}
										</p>
										
									</section>
									<section class="box">
										<header>
											<h3>Dates sorties</h3>
										</header>
										
										<ul class="divided">
											<li>au: {{currentAmiibo.release.au}}</li>
											<li>jp: {{currentAmiibo.release.jp}}</li>
											<li>eu: {{currentAmiibo.release.eu}}</li>
											<li>na: {{currentAmiibo.release.na}}</li>
											<li></li>
											<li></li>
										</ul>
										
									</section>

							</div>
							<div class="col-8 col-12-medium imp-medium">

								<!-- Content -->
									<article class="box post">
										<a href="#" class="featured"><img :src='currentAmiibo.image' alt="" /></a>
										<header>
											<h2>{{currentAmiibo.name}}</h2>
											<p>{{currentAmiibo.type}}</p>
										</header>
										
										
										
									</article>

							</div>
						</div>
					</div>
				</section>
</template>

<style>

</style>
