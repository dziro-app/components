<!--D Componente para seleccionar una colección -->
<script lang="ts" >
  import Color from "color"
  import {getUiColors} from "../Utils/colors"

  export let name: string // Nombre de la colección
  export let color: string // Color de la colección
  export let emoji: string // Emoji de la colección

</script>

<div
  on:click
  style={`background: ${color}`}
  class="CollectionButton">
  <div class="iconWrapper">
    {emoji}
  </div>
  <div 
    style={`color: ${getUiColors(color).text}`}
    class="name">
    {name}
  </div> 
</div>

<style lang="scss" >
  @import "../Styles/_colors.scss";
  @import "../Styles/_texts.scss";

  .CollectionButton {
    align-items: center;
    box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.05);
    cursor: pointer;
    display: flex;
    transition: all 0.3s;
    padding: 12px 16px;

    &:hover {
      box-shadow: 0 4px 4px 0 rgba(0, 0, 0, 0.25);
    }
  }

  .iconWrapper {
    align-items: center;
    background: $white;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    height: 29px;
    width: 29px;
  }

  .name {
    @include normal-text;
    margin-left: 16px;
  }
</style>

<!--E
<CollectionButton name='Bandeja' color='#EDE63E' emoji='🛒' />
<CollectionButton name='Bandeja' color='#4f0b0b' emoji='🛒' />
-->