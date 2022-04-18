<!--D Componte para mostrar un artículo -->
<script lang="ts">
  import Icon from "./Icon.svelte"

  export let image: string // Imagen del artículo
  export let name: string // Nombre del artículo
  export let website: string // Url del artículo
  export let price: number // Precio del artículo

  const getDisplayLink = (url: string) => {
    const res = url.match(/http[s]?:\/\/[\w.]+/i)
    console.log(res)
    if (res.length > 0) {
      return res[0].split("//")[1]
    }
    return "---"
  }
  
</script>

<div class="Item">
  <img src={image} alt="preview" />

  <div class="info">

    <div class="name"> {name} </div>
    <a  class="website" target="_blank" href={website}>
      <Icon size={16} name="globe" /> { getDisplayLink(website)}
    </a>
    
  </div>

  <div class="price">
    $ {price}
  </div>
</div>

<style lang="scss">
  @import "../Styles/_colors.scss";
  @import "../Styles/_sizing.scss";
  @import "../Styles/_texts.scss";
  @import "../Styles/_item.scss";

  .Item {
    @include item-card;
    background: $white;
    box-shadow: 0 1px 1px 1px $smoke;

    img {
      display: block;
      height: 175px;
      margin: 0 auto;
      object-fit: scale-down;
      width: 96%;
    }

    .info {
      padding: sizing(2) 0 sizing(2) 0;

      .name {
        @include subtitle;
        font-size: 18px;
      }

      .website {
        @include small-text;
        align-items: center;
        display: flex;
        color: inherit;
        grid-gap: 0.5em;
        margin-top: 0.6em;
        &:hover, &:visited {
          color: inherit;
        }
      }
    }
    .price {
      @include subtitle;
      text-align: center;
    }

    &:hover {
      box-shadow: 0 1px 4px 1px $smoke;
    }
  }
</style>

<!--E
<CollectionItem 
  name='Guía de arquitectura Ciudad de México | Arquine'
  website='https://www.arquine.com/libros/guia-de-arquitectura-ciudad-de-mexico/'
  image='https://www.arquine.com/wp-content/uploads/2015/04/guia1.jpg' 
  price={29.00} />
-->