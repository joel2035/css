# documentation

##convension BEM
* B => Block
* E => Element
* M => Modifier

```html
<!-- main list  -->
<ul class = "mainList">
<!-- itemLink = Element -->
  <li class="mainList_item">
    <!-- itemLink = Element -->
    <a class= "mainList_itemLink mainList_itemLick--isActive"href="/home">home</a>
  </li>
  <li class="mainList_item ">
    <!-- itemLink = Element -->
    <a class= "mainList_itemLink "href="/About">About</a>
  </li>

  <li class="mainList_item">
    <!-- itemLink = Element -->
    <a class= "mainList_itemLink"href="/Works">works</a>
  </li>
</ul>
```
```css
.mainList{
  display:flex;
  justify-content:space-between
  &--xmas{
    background: green;
  }
  &__item{
    list-style:none
  }
  &__itemLink{
    color:red;
    &--isActive{
      color:white
    }
  }
}
/* Exemple en css du rendu */
```css
.mainList{

}
.mainList--max{

}
.mainList_item{

}
.mainList_itemLick{

}
```
les pseudo attributs `before`et `after` permettent de créer des noueds HTML en CSS.
Ils sont essentiellement utilisés pour ajouter des ornements , des décorations ... On  peut bien entendu faire des animations avec, les positioner par rapport à ler parent (relative/ absolute). *** Ils doivent obligatoirement avoir un `content: ''`** afin de s'afficher
```HTML
<section class="cover">
  <h1 class="cover_mainTitle">Presentation des pseudo-attributs</h1>


</section>
```
```CSS
.cover{
  background: #FDFDFD;
  padding: 20px;
  &_mainTitle{
    text-align:center;,
    font-size: 24px;
    color: green;
    position: relative;
    &::before,
    &::after{
position:absolute;
      content:"";
      display: block;
      width: 50px;
      height: 50px;
      background: green;
      top:0;
      color:#FFFFFF;
    }
    &::before{
      left: 0;
    }

    &::after{
      right: 0;
    }
  }
}
```CSS
.cover{
  font-size: 16px;
  &_mainTitle{
/*  1em = 16px/ .8em <> 16px;*/
    font-size: .8em;

  }
}
```
## REM, EM, %, VW Sizing
### %
### EM
### REM



* le remest basé sur la taille de la racine (soit la balise <html>) qui , par défaut a une valeur de 16px. Afin d'évitertout calcul, il est nécessaire de l'écraser en donnant une base de 10px soit 62.5%.
*  le REM est intéressant à utilser si les media- queries employer sont en rem egalement.
cela vous permettra egalement de garder des proportion égales lorsqu'on va redimentionner la page.
*  ses proportionnseront également garder quand l'utilisateur zoomera dans votre page

  ```CSS


html {
  font-size:62,5%;  
  /*  pour que la taille de notre soit de 10px en tout temps  */
}
.__mainTitle{
  font-size: 1.6em;
  width: 32em;
}
```

### vw(idth)/VH(eight)
* unites relatives à la taille de votre écran (peu importe le devise )
* Attention au VH et à son contenu. 100vh === 100vh quoi qu'il arrive.
* VW : très utile pour les interfaces fluides.
## Liens utiles
* Liens utiles :
*
# css
