<!--D Componente para preview de una colección -->

<script lang="ts">
  import { fly } from 'svelte/transition'

  import Color from "color"
  import Icon from "./Icon.svelte"

  type Option = {
    display: string,
    onClick: Function
  }

  export let name: string // Nombre de la colección
  export let color: string // Color de la colección
  export let emoji: string // Emoji de la colección
  export let options: Array<Option> = [] // Array de opciones para el menú

  let showOptions = false

  const onDefaultOptionClick = (option: Option) => {
    showOptions=false
    option.onClick()
  }


</script>

<div style={`background: ${Color(color).lightness(60).desaturate(0.3).lighten(0.5)}`}>
  <div 
    class="header"
    style={`background: ${color}`}>
    <div class="iconWrapper">
      {emoji}
    </div>
    <h3 style={`color: ${Color(color).darken(0.35).desaturate(0.5).saturate(0.1)}`} > 
      {name}
    </h3>
    <div class="menu">
      <Icon 
      on:click={() => { showOptions = !showOptions }}
      color={Color(color).darken(0.35).desaturate(0.5).saturate(0.1)} />
      {#if showOptions}
        <div class="options" transition:fly="{{ y: -10 }}">
          { #each options as option }
            <div class="option" on:click={() => onDefaultOptionClick(option)} > {option.display} </div>
          {/each}
        </div>
      {/if}
    </div>
  </div>

  <div class="content">
    <slot></slot>
  </div>
</div>

<style lang="scss">
  @import "../Styles/_texts.scss";
  @import "../Styles/_colors.scss";
  @import "../Styles/_sizing.scss";

  .header {
    align-items: center;
    display: grid;
    grid-template-columns: 36px 1fr 20px;
    padding: 24px;

    .iconWrapper {
      align-items: center;
      background: $white;
      border-radius: 50%;
      display: flex;
      font-size: 24px;
      height: 36px;
      justify-content: center;
      width: 36px;
    }
    h3 {
      font-size: 36px;
      font-family: 'Raleway', sans-serif;
      margin: 0;
      margin-left: 16px;
    }

    .menu {
      cursor: pointer;
      position: relative;
    }

    .options {
      background: $black;
      position: absolute;
      color: $white;
      right: 0;
      top: 100%;
      padding: 10px 5px;

      .option {
        @include mini-text;
        cursor: pointer;
        padding: 0.5em 5px;
        &:hover {
          background: $white;
          color: $black;
        }
      }
    }
    
  }

  .content {
    padding: sizing(6) sizing(4);
  }
</style>

<!--E
<CollectionDetail 
  name='Bandeja' color='#EDE63E' emoji='🛒'
  options={[{'display': 'Eliminar', onClick: ()=>{ alert('Eliminar') }}]}>
  Con un solo color calculamos el resto.
</CollectionDetail>
-->