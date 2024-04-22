
<script>
//Esta es una forma de hacer una peticion en SVELTE
  let listdata=[];
 //fetch('https://jsonplaceholder.typicode.com/users')
    fetch ('http://127.0.0.1:5004/project/')
        .then((response) => response.json())
        .then((results) => listdata=results)
  
  
  </script>
  
  
      <ul>
      {#each listdata as values }
          <li>{values.company.name}</li>
      {/each}
      </ul>
 

  

