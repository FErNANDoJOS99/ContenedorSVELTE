

<script>
    //ESTA ES LA SEGUNDA FORMA DE HACER UNA PETICION EN SVELTE
    import { onMount } from 'svelte';
    let data;
    async function fetchData() {
      try {
    
      //const response = await fetch('https://jsonplaceholder.typicode.com/users')
        const response = await fetch ('http://127.0.0.1:5004/project/')
        if (!response.ok) {
          throw new Error('Error al cargar los datos');
        }

        data = await response.json();
      } catch (error) {
        console.error(error);
      }
    }
   onMount(fetchData);
  
  </script>
  
  hola
  {#if data}
    <ul>
      {#each data as item}
        <li>{item.company.name}</li>
      {/each}
    </ul>
  {:else}
    <p>Cargando...</p>
  {/if}
  