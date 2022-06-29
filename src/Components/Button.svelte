<!--D Componente para botón -->
<script lang='ts'>
  export let form: "outline" | "normal"  = "normal"
  export let type: "button" | "submit" = "button"
</script>

<button 
  class:outline={form==="outline"}
  class:normal={form==="normal"}
  type={type}
  on:click>
  <slot></slot>
</button>


<style lang="scss">
  @use "../Styles/colors.scss";
  @import "../Styles/_texts.scss";

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
      padding: 16px 64px;
      transition: all 0.3s;
      &:hover {
        box-shadow: 0 4px 4px rgba(0, 0, 0, 0.25);
      }
    }

    &.outline {
      border: 2px dashed colors.$base-color-black-80;
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
<Button form='outline' > Outline </Button>
<Button> Normal </Button>
-->
