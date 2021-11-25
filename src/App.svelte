<script>
	import SvelteLogo from './pages/SvelteLogo.svelte';
  import { Router, Route } from "svelte-routing";
  import NavBar from "./components/NavBar.svelte";
  import AboutPage from "./pages/AboutPage.svelte";
  import HomePage from "./pages/HomePage.svelte";
  export let url = "";
</script>

<Router {url}>
  <NavBar />
  <div class="container">
    <Route exact path="/"><HomePage /></Route>
    <Route  path="about"><AboutPage /></Route>
    <Route  path="info"><SvelteLogo /></Route>
  </div>
</Router>

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
