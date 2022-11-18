<script setup>

import { onBeforeMount,ref } from 'vue'
import axios from 'axios'
import TheBanner from '../components/TheBanner.vue';

const API_AMIIBO = 'https://www.amiiboapi.com/api/amiibo/'

const amiiboFav = ref({})

onBeforeMount(async ()=>{

  const amiibo = await axios.get(API_AMIIBO)
  const {data,status} = amiibo // object destructuring FTW!
  if(status===200){
      // isDataLoading.value=false
  }
  console.log(data)
  amiiboFav.value = data.amiibo
     
})

</script>

<template>
        <!-- Banner -->
        <TheBanner />
				<section id="intro" class="container">
					<div class="row">
						<div class="col-4 col-12-medium">
							<section class="middle">
								<img :src='amiiboFav[0].image' />
								<header>
									<h2>{{ amiiboFav[0].character }}</h2>
								</header>
								<p>{{ amiiboFav[0].gameSeries }}</p>
							</section>
						</div>
						<div class="col-4 col-12-medium">
							<section class="middle">
								<img :src='amiiboFav[10].image' />
								<header>
									<h2>{{ amiiboFav[10].character }}</h2>
								</header>
								<p>{{ amiiboFav[10].gameSeries }}</p>
							</section>
						</div>
						<div class="col-4 col-12-medium">
							<section class="middle">
								<img :src='amiiboFav[60].image' />
								<header>
									<h2>{{ amiiboFav[60].character }}</h2>
								</header>
								<p>{{ amiiboFav[60].gameSeries }}</p>
							</section>
						</div>
					</div>
					<footer>
						<ul class="actions">
							<li><RouterLink to="/liste">Liste complète</RouterLink></li>
						</ul>
					</footer>
				</section>
</template>
