<script>
    //ESTE ES UN INTENTO FALLIDO DE COMUNICARME A LA API DE OPENWEATHER 
    import { onMount } from 'svelte';
  
    // Definir una variable para almacenar los datos de la API
    let data = [];
  
    // Función para realizar la solicitud a la API
    async function fetchData() {
      try {
        // Realizar la solicitud a la API
        const response = await fetch('https://api.openweathermap.org/data/2.5/weather?lat=19.3371&lon=-99.566&appid=79b3a0ad9259f2b8e1d8ab365924fc95');
        
        // Verificar si la solicitud fue exitosa
        if (!response.ok) {
          throw new Error('No se pudo obtener los datos');
        }
        
        // Parsear la respuesta como JSON
        data = await response.json();
      } catch (error) {
        console.error(error);
      }
    }
  
    // Llamar a la función fetchData() cuando el componente se monta
    onMount(fetchData);
  </script>
  
  <main>
    <h1>Datos de la API:</h1>
    {#if data.length > 0}
      <!-- Mostrar los datos de la API -->
      <ul>
        {#each data as item}
          <li>
            <!-- Mostrar cada objeto JSON dentro de un item de la lista -->
            <ul>
              {#each Object.keys(item) as key}
                <li>{key}: {item[key]}</li>
              {/each}
            </ul>
          </li>
        {/each}
      </ul>
    {:else}
      <p>Cargando...</p>
    {/if}
  </main>
  
  