<!--D Componente para emoji -->
<script type="ts">
  import emojis from "emojis-list"
  import Icon from "./Icon.svelte"
  export let label: string = ""
  export let name: string
  export let value = ""

  let showOptions = false

  const onChange = (emojiValue) => {
    value = emojiValue
    showOptions = false
  }

  import BaseInput from "./InputBase.svelte"
</script>

<div class="EmojiInput">
  <BaseInput label={label} name={name} >
    <div class="display" >
      <span>
        {#if value === ""}
          <span class="placeholder">{label}</span>
        {:else}
          {value}
        {/if}
      </span>
      <div 
        class="trigger" 
        class:open={showOptions}
        on:click={() => {showOptions = !showOptions}} >
        <Icon size={22} color="#000" name="CaretDown" />
      </div>
    </div>
    {#if showOptions}
      <div class="options">
        {#each emojis as emoji}
        <div class="option" on:click={() => { onChange(emoji) }}> {emoji} </div>
        {/each}
      </div>
    {/if}
    <input
      readonly
      id={name} name={name} placeholder={label} 
      bind:value={value} type="hidden">
  </BaseInput>
</div>

<style lang="scss">
  @import "../Styles/_inputs.scss";
  @import "../Styles/_sizing.scss";

  .EmojiInput{
    position: relative;
    .display {
      @include input;
      display: flex;
      align-items: center;
      justify-content: space-between;
      .trigger {
        align-items: center;
        background: $white;
        transition: all 0.3s;
        border-radius: 50%;
        cursor: pointer;
        justify-content: center;
        display: flex;
        height: 30px;
        width: 30px;

        &.open {
          transform: rotateZ(180deg);
        }
      }
    }

    .placeholder {
      color: $gray;
    }
    

    .options {
      background: $smoke;
      display: flex;
      flex-wrap: wrap;
      padding: sizing(1);
      font-size: 30px;
      max-height: 200px;
      left: 0;
      overflow-y: scroll;
      position: absolute;
      top: 100%;
      z-index: 2;
      
      .option {
        cursor: pointer;
        padding: sizing(1);
        border-radius: 5px;
        &:hover {
          outline: 1px solid $gray;
        }
      }
    }
  }
</style>
<!--E
<InputEmoji name='emoji' label='Emoji' />
-->
