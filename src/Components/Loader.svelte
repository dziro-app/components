<!--D Componente de loader -->
<script lang="ts">
  export let size = 24 // Tamaño del loader
  export let color = "#000" // Color del loader
</script>

<svg 
  class="Loader" width={size} height={size}
  viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M2 12C2 6.47715 6.47715 2 12 2V5C8.13401 5 5 8.13401 5 12H2Z" 
  fill={color}/>
</svg>

<style lang="scss" >

  @keyframes spinAround {
    from {transform:rotate(0deg);}
    to {transform:rotate(360deg);}
  }
  
  .Loader {
    animation: 1s linear 0s normal none infinite spinAround;
  }
</style>

<!--E
 <Loader size={30} />
 <Loader size={20} color='red' />
 <Loader size={10} color='green' />
-->