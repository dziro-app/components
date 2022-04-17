<!--D Menu del header para usuario pro -->
<script lang='ts' >
  import Icon from "./Icon.svelte"

  type Option = {
    display: string,
    onClick: Function
  }

  export let  username: string // Nombre del usuario
  export let picture: string // Url del perfil del usuario
  export let options: Array<Option> = [] // array de opciones para el menú

  let isOpen = false

  const onDefaultOptionClick = (option: Option) => {
    isOpen=false
    option.onClick()
  }

</script>

<div class="Menu">
  <div class="info" >
    <img class="profilePic" src={picture} alt="profile_image">
    <span class="username" > {username} </span>
    <div 
      class="trigger"
      class:open={isOpen}
      on:click={() => { isOpen = !isOpen }}>
      <Icon name="CaretDoubleDown" />
    </div>
  </div>
  {#if isOpen && options.length > 0}
    <div class="options">
      { #each options as option }
        <div class="option" on:click={() => onDefaultOptionClick(option)} > {option.display} </div>
      {/each}
    </div>
  {/if}
</div>

<style lang="scss" >
  @import '../Styles/_colors.scss';
  @import "../Styles/_sizing.scss";
  @import "../Styles/_texts.scss";
  .Menu {
    border: 2px solid $white;
    color: $white;
    display: inline-block;
    padding: sizing(1) 5px;
    position: relative;
    .info {
      align-items: center;
      display: flex;
      justify-content: center;
    }

    .profilePic {
      object-fit: cover;
      height: 30px;
      width: 30px;
    }
    .username {
      padding: 0 20px;
      font-size: 20px;
      font-family: 'Raleway', sans-serif;
    }
    .trigger {
      cursor: pointer;
      transition: all 0.3s;
      width: 26px;
      &.open {
        transform: rotateZ(180deg);
      }
    }
    .options {
      @include small-text;
      background: $black;
      box-sizing: border-box;
      left: 0;
      padding: 10px 5px;    
      position: absolute;
      top: 105%;
      width: 100%;
      z-index: 3;
      .option {
        padding: 0.5em 5px;
        &:hover {
          background: $white;
          color: $black;
          cursor: pointer;
        }
      }
    }
  }
</style>


<!--E
<div style='background: #000; padding: 1em;' >
  <UserMenu
    username='evesan' 
    picture='https://scontent.fmex23-1.fna.fbcdn.net/v/t39.30808-1/278564546_10227806627133607_7727109533929761911_n.jpg?stp=dst-jpg_p320x320&_nc_cat=103&ccb=1-5&_nc_sid=7206a8&_nc_ohc=ePMaBe8wRcgAX_JDGQu&_nc_ht=scontent.fmex23-1.fna&oh=00_AT8sxOy6t1oBN8_xBfL-pIKTx6ay3-oG8VLJyKPXtr0HDA&oe=62603FE5'
    options={[{'display': 'Acerca de', onClick: ()=>{ alert('acerca de') }}]}
  />
</div>
-->