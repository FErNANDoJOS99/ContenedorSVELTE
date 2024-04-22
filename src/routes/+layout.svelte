<script>
    import "../app.css";
    import NavBar from "../components/NavBar/NavBar.svelte";
   
</script>
  
<NavBar />
  <slot />

<div id="abajo">
  <NavBar />
  
</div>  
  
<style>

  #abajo{
    position:fixed;
    width: 100%;
    bottom: 0;
  }

</style>

