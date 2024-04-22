<script>
  let cadena = "Hola, servidor!";

  async function enviarDatos() {
    try {
      // Realizar la solicitud POST al servidor
      const response = await fetch('https://www.facebook.com/?locale=es_LA', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json' // Especifica el tipo de contenido como JSON
        },
        body: JSON.stringify({ cadena }) // Convierte el objeto JavaScript a una cadena JSON
      });

      if (!response.ok) {
        throw new Error('Error en la solicitud');
      }

      const data = await response.text(); // Obtener la respuesta del servidor como texto
      console.log('Respuesta del servidor:', data);
    } catch (error) {
      console.error('Error:', error);
    }
  }
</script>

<button on:click={enviarDatos}>Enviar Datos</button>
