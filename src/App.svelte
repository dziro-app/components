<script>
  import LogoComponent from "./Components/Logo.svelte"

  // Common components
  import Logo from "./Docs/Pages/Logo.svelte"
  import Button from "./Docs/Pages/Button.svelte"
  import Header from "./Docs/Pages/Header.svelte" 
  import UserMenu from "./Docs/Pages/UserMenu.svelte"

  // Collection
  import CollectionButton from "./Docs/Pages/CollectionButton.svelte"
  import CollectionDetail from "./Docs/Pages/CollectionDetail.svelte"
  import CollectionItem from "./Docs/Pages/CollectionItem.svelte"
  import CollectionAddItem from "./Docs/Pages/CollectionAddItem.svelte"

  // Inputs
  import InputText from "./Docs/Pages/InputText.svelte"
  import InputColor from "./Docs/Pages/InputColor.svelte"
  import InputEmoji from "./Docs/Pages/InputEmoji.svelte"

  // Misc
  import ModalBase from "./Docs/Pages/ModalBase.svelte"
  
  let CurrentComponent = CollectionItem
  
  const componentMap = [{
    name: "Logo",
    component: Logo
  }, {
    name: "Button",
    component: Button
  }, {
    name: "Header",
    component: Header
  }, {
    name: "UserMenu",
    component: UserMenu
  }, {
    name: "CollectionButton",
    component: CollectionButton
  }, {
    name: "CollectionDetail",
    component: CollectionDetail
  }, {
    name: "CollectionAddItem",
    component: CollectionAddItem
  }, {
    name: "CollectionItem",
    component: CollectionItem
  }, {
    name: "InputText",
    component: InputText
  }, {
    name: "InputColor",
    component: InputColor
  }, {
    name: "InputEmoji",
    component: InputEmoji
  }, {
    name: "ModalBase",
    component: ModalBase
  }]

  const seeComponent = (index) => {
    CurrentComponent = componentMap[index].component
  }
</script>

<main>
  <div class="left">
    <LogoComponent />
    {#each componentMap as compo, i}
      <p on:click={ () => {seeComponent(i)}} > {compo.name} </p>
    {/each}
  </div>
  <div class="right">
    <svelte:component this={CurrentComponent}/>
  </div>
</main>

<style lang='scss'>
  @import './Styles/colors.scss';

  :global(body) {
    margin: 0;
    padding: 0;
  }

  main {
    display: grid;
    grid-template-columns: 260px 1fr;
  
    .left {
      background: $black;
      color: $smoke;
      min-height: 100vh;
      padding: 1em;
      p {
        cursor: pointer;
        text-align: center;
        &:hover {
          color: $white;
        }
      }
    }
  }
</style>
