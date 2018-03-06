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

## Les effets CSS3 sur les images

```HTML
<div class="zoom colonne">
<div>
<div><img src="images/img1.jpg" /></div>
</div>
<div>
<div><img src="images/img2.jpg" /></div>
</div>
<div>
<div><img src="images/img3.jpg" /></div>
</div>
</div>
```
```CSS
/* mise en forme css  */
.colonne {
	margin: 15px 25px 0 25px;
	padding: 0;
}
.colonne:last-child {
	padding-bottom: 60px;
}
.colonne::after {
	content: '';
	clear: both;
	display: block;
}
.colonne div {
	position: relative;
	float: left;
	width: 200px;
	height: 150px;
	margin: 0 0 0 35px;
	padding: 0;
}
.colonne div:first-child {
	margin-left: 0;
}
div {
	width: 200px;
	height: 150px;
	margin: 0;
	padding: 0;
	background: #F4F4F4;
	overflow: hidden;}
  .zoom div img {
	-webkit-transform: scale(1);
	transform: scale(1);
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
/* Pour zoomer */
.zoom div img {
	-webkit-transform: scale(1);
	transform: scale(1);
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
.zoom div:hover img {
	-webkit-transform: scale(1.3);
	transform: scale(1.3);
}

/* Pour Dézoomer */

.zoom-out div img {
	-webkit-transform: scale(1.25);
	transform: scale(1.25);
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
.zoom-out div:hover img {
	-webkit-transform: scale(1);
	transform: scale(1);
}
/* Pour arondir mes images */
.rounded div img {
  width: 200px; /* largeur de l'image */
  height: auto; /* hauteur de l'image */
  -webkit-transition: .3s ease-in-out !important;
  transition: .3s ease-in-out !important;
}
.rounded div:hover img:hover {
  width: 150px; /* on affiche l'image au carré */
  height: 150px;
  border-radius: 50%;
}

/* slide d'image */
.slide div img {
	margin-left: 0px;
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
.slide div:hover img {
	margin-left: -30px;
}
/* rotation et dézoomé*/
.rotate-zoom-out div img {
	-webkit-transform: rotate(10deg) scale(1.25);
	transform: rotate(10deg) scale(1.25);
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
.rotate-zoom-out div:hover img {
	-webkit-transform: rotate(0) scale(1);
	transform: rotate(0) scale(1);
}


/*flou*/
.blur div img {
	-webkit-filter: blur(3px);
	filter: blur(3px);
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
.blur div:hover img {
	-webkit-filter: blur(0);
	filter: blur(0);
}

/* noir et blanc puis couleur au hover*/
.grayscale div img {
	-webkit-filter: grayscale(100%);
	filter: grayscale(100%);
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
.grayscale div:hover img {
	-webkit-filter: grayscale(0);
	filter: grayscale(0);
}

/* sépia (la couleur se montre au hover)*/
.sepia div img {
	-webkit-filter: sepia(100%);
	filter: sepia(100%);
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
.sepia div:hover img {
	-webkit-filter: sepia(0);
	filter: sepia(0);
}

/* Morph (arrondir les images et les faires tourné sur elle même) */
.morph div img {
  width: 200px;
  height: 150px;
  -webkit-filter: grayscale(0) blur(0px);
  filter: grayscale(0) blur(0px);
  -webkit-transition: all 0.5s ease;
  transition: all 0.5s ease;
}

.morph div:hover img {
  width: 150px; /* on affiche l'image au carré */
  height: 150px;
  border-radius: 50%;  /* on arrondit l'image */
  -webkit-transform: rotate(360deg); /* rotation de l'image */
  transform: rotate(360deg);
}
/* L'Opacité */
.opacity1 div img {
	opacity: 1;
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
.opacity1 div:hover img {
	opacity: .5;
}
/* Opacité colorer */
.opacity-color div {
background: #184a7d;
}
.opacity-color div img {
	opacity: 1;
	-webkit-transition: .3s ease-in-out;
	transition: .3s ease-in-out;
}
.opacity-color div:hover img {
	opacity: .5;
}
/* Flash */
.flash div:hover img {
	opacity: 1;
	-webkit-animation: flash 1.5s;
	animation: flash 1.5s;
}
@-webkit-keyframes flash {
	0% {
		opacity: .4;
	}
	100% {
		opacity: 1;
	}
}
@keyframes flash {
	0% {
		opacity: .4;
	}
	100% {
		opacity: 1;
	}
}
/* refelt (pour ajouter les reflet sur mes images) */
.shine div {
	position: relative;
}
.shine div::before {
	position: absolute;
	top: 0;
	left: -75%;
	z-index: 2;
	display: block;
	content: '';
	width: 50%;
	height: 100%;
	background: -webkit-linear-gradient(left, rgba(255,255,255,0) 0%, rgba(255,255,255,.3) 100%);
	background: linear-gradient(to right, rgba(255,255,255,0) 0%, rgba(255,255,255,.3) 100%);
	-webkit-transform: skewX(-25deg);
	transform: skewX(-25deg);
}
.shine div:hover::before {
	-webkit-animation: shine .75s;
	animation: shine .75s;
}
@-webkit-keyframes shine {
	100% {
		left: 125%;
	}
}
@keyframes shine {
	100% {
		left: 125%;
	}
}
/* Halo de lumière */
.light div {
	position: relative;
}
.light div::before {
	position: absolute;
	top: 50%;
	left: 50%;
	z-index: 2;
	display: block;
	content: '';
	width: 0;
	height: 0;
	background: rgba(255,255,255,.2);
	border-radius: 100%;
	-webkit-transform: translate(-50%, -50%);
	transform: translate(-50%, -50%);
	opacity: 0;
}
.light div:hover::before {
	-webkit-animation: circle .75s;
	animation: circle .75s;
}
@-webkit-keyframes circle {
	0% {
		opacity: 1;
	}
	40% {
		opacity: 1;
	}
	100% {
		width: 200%;
		height: 200%;
		opacity: 0;
	}
}
@keyframes circle {
	0% {
		opacity: 1;
	}
	40% {
		opacity: 1;
	}
	100% {
		width: 200%;
		height: 200%;
		opacity: 0;
	}
}
```
