<!--D Componente para botón -->
<script lang='ts'>
  import Loader from "./Loader.svelte"

  export let form: "outline" | "normal"  = "normal" // Estilo del botón
  export let type: "button" | "submit" = "button" // Tipo de botón
  export let loading: boolean = false // Bandera q  ue indica el loading
</script>

<button 
  class:outline={form==="outline"}
  class:normal={form==="normal"}
  class:loading={loading}
  type={type}
  on:click>
  {#if loading}
    <Loader size={18} color="#fff" />
  {:else}
    <slot></slot>
  {/if}
</button>


<style lang="scss">
  @use "../Styles/colors.scss";
  @import "../Styles/_texts.scss";
  @import "../Styles/_sizing.scss";

  button {
    @include  normal-text;
    background: none;
    border-radius: 5px;
    border: none;
    cursor: pointer;

    &.normal {
      background: colors.$base-color-black-80;
      box-shadow: 0 4px 4px rgba(0, 0, 0, 0.06);
      color: colors.$base-color-white-100;;
      padding: sizing(2) sizing(8);
      transition: all 0.3s;
      &:hover {
        box-shadow: 0 4px 4px rgba(0, 0, 0, 0.25);
      }
      &.loading{
        background-color: colors.$base-color-gray-60;
        padding: sizing(2) sizing(8);
      }
    }

    &.outline {
      border: 2px dashed colors.$base-color-gray-60;
      border-radius: 6px;
      color: colors.$base-color-gray-60;
      font-size: 18px;
      opacity: 0.8;
      transition: all linear 0.3s;
      padding: 16px;
      &:hover {
        background: colors.$base-color-white-50;
        opacity: 1;
      }
    }
  }
</style>

<!--E
<Button form='outline' loading > Outline </Button>
<Button form='outline' > Outline </Button>
<Button> Normal </Button>
<Button loading > Normal </Button>
-->
