<!--D Header -->
<script lang="ts">
  export let  username: string // Nombre del usuario
  export let picture: string // Url del perfil del usuario
  export let options = [] // Opciones que se pasarán al componente de menú


  import Logo from './Logo.svelte'
  import Menu from './UserMenu.svelte'

</script>

<header>
  <div class="logo_wrapper">
    <Logo />
  </div>
  <div>
    {#if username && picture}
      <Menu 
        username={username}
        picture={picture}
        options={options}
        />
    {/if}
  </div>
</header>

<style lang="scss" >
  @import '../Styles/_colors.scss';
  @import '../Styles/_sizing.scss';
  header {
    align-items: center;
    background: $black;
    box-sizing: border-box;
    display: flex;
    justify-content: space-between;
    padding: 0px 10px;
    height: $nav-height;
  }
</style>

<!--E
<Header />
<br>
<Header 
  username='evesan' 
  picture='https://scontent.fmex23-1.fna.fbcdn.net/v/t39.30808-1/278564546_10227806627133607_7727109533929761911_n.jpg?stp=dst-jpg_p320x320&_nc_cat=103&ccb=1-5&_nc_sid=7206a8&_nc_ohc=ePMaBe8wRcgAX_JDGQu&_nc_ht=scontent.fmex23-1.fna&oh=00_AT8sxOy6t1oBN8_xBfL-pIKTx6ay3-oG8VLJyKPXtr0HDA&oe=62603FE5'
  options={[{'display': 'Acerca de', onClick: ()=>{ alert('acerca de') }}]}
/>
-->
