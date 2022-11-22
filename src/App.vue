<template>
  <div id="app">
<body class="homepage is-preload">
		<div id="page-wrapper">

			<!-- Header -->
				<div id="header-wrapper">
					<div class="container">

						<HeaderView />
						<!-- Banner -->
							<div id="banner">
								<h2><strong>Magic Card:</strong> Ma collection </h2>
							</div>

					</div>
				</div>
 
  <router-view />


			<FooterView />

		</div>

	</body>
  </div>
</template>

<script>
import HeaderView from "@/components/HeaderComponent.vue"
import FooterView from "@/components/FooterComponent.vue"

  export default{
   
  components:{
      HeaderView,FooterView
  }
  }
</script>



<style>

@import url("./assets/style/main.css");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}


</style>
