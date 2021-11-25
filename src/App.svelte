<script>
  import Router from "svelte-spa-router";
  import NavBar from "./components/NavBar.svelte";
  import AboutPage from "./pages/AboutPage.svelte";
  import HomePage from "./pages/HomePage.svelte";
  import SvelteLogo from './pages/SvelteLogo.svelte';
</script>


  <NavBar />
  <div class="container">
	<Router routes={{
		'/': HomePage,
		'/about': AboutPage,
		'/info': SvelteLogo
	}}/>
  </div>

<style>
  :global(*, html, body) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  :global(a) {
    text-decoration: none;
  }

  :global(li) {
    list-style: none;
  }

  :global(.container) {
    max-width: 95%;
    margin: 0 auto;
  }

  :global(.row) {
    display: flex;
  }
  :global(.jcsb) {
    justify-content: space-between;
  }
  :global(.aic) {
    align-items: center;
  }
</style>
