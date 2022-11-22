<template>
    	<div class="col-4 col-12-medium">
											<section>
												<a href="#" class="image featured"><img src="images/pic01.jpg" alt="" /></a>
												<header class="second icon solid fa-dragon">
													<h3>Titre de la carte</h3>
													<p>And a subtitle</p>
												</header>
											</section>
										</div>

</template>


<script> 
export default{
 name:"Card",
 data:()=>({
 }),
props: {
title: {
      type: String,
      required: true,
default:"pas de titre"
    },
   subTitle: {
      type: String,
      required: true,
default:"pas de soustitre"
    }
 

}
}
</script>

<style scoped>
 
</style>