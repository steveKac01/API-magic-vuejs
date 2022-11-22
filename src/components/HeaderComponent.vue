<template>
  
							<header id="header">
								<div class="inner">

									<!-- Logo -->
										<h1  @click="goToHome()">Magic</h1>

									<!-- Nav -->
										<nav id="nav">
											<ul>
												<li @click="goToHome()" class="router-link"> Home </li>
												<li @click="goToCollection()"> Ma Collection </li>
											</ul>
										</nav>

								</div>
							</header>


</template>

<script>
 

export default{
 name:"HeaderView",
 data:()=>({
 }),
 methods:{
     goToHome(){
         this.$router.push({name:"home"})
     },
     goToCollection()
     {
          this.$router.push({name:"collection"})
     }
 }
 

}
</script>

<style scoped>
h1,li{
    cursor: pointer;
}
 .router-link-exact-active { /*Marche pas :| */
   color:red ;
 }
 
</style>