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
## flexboxgrid

col-xs-(nombre de colonnes) : Mobile

col-md-(nombre de colonnes) : Tablette

col-lg-(nombre de colonnes) : Desktop

ALIGNEMENTS

.start- : à gauche

.center- : au millieu

.end- : à droite

(Plus ou moins)
## L'UTILISATIONS DES GRILLE FLEXBOX

# Sensible
Les modificateurs réactifs permettent de spécifier différentes tailles de colonnes, décalages, alignement et distribution aux largeurs de la fenêtre xs, sm, md & lg.
```html
<div class="row">
    <div class="col-xs-12
                col-sm-8
                col-md-6
                col-lg-4">
        <div class="box">Responsive</div>
    </div>
</div>
```
#POUR QU'IL SOIT FLUIDE
```CSS
.col-xs-6 {
  flex-basis: 50%;
}
```
# Pour décaler les colone
```HTML
<div class="row">
    <div class="col-xs-offset-3 col-xs-9">
        <div class="box">offset</div>
    </div>
</div>
```
# Pour des largeurs automatiques
```HTML
Ajoutez n'importe quel nombre de colonnes de dimensionnement automatique à une ligne. Laissez la grille le découvrir.


<div class="row">
    <div class="col-xs">
        <div class="box">auto</div>
    </div>
</div>
```

# Grilles imbriquées
```html
Les grilles Nest à l'intérieur des grilles à l'intérieur des grilles.
<div class="row">
    <div class="col-xs">
        <div class="box">
            <div class="row">
                <div class="col-xs">
                    <div class="box">auto</div>
                </div>
            </div>
        </div>
    </div>
</div>
pour autre chose allez sur http://flexboxgrid.com/
```

### JavaScript mémo

Le HTML

```html

<section id="sectionId" class="firstSection">
   <h2 class="firstSection_title">Le titre</h2>
   <img class="firstSection_Img" src="" alt="">
   <div class="firstSection_container">
      <p class="firstSection_containerText">Coucou</p>
      <p class="firstSection_containerText">Toi</p>
   </div>

   <button data-number="1" type="button" name="button">Bouyah</button>
   <button data-number="2" type="button" name="button">Hola</button>
   <button data-number="3" type="button" name="button">Hey</button>
   <article class="firstSection_article">
      <img src="" alt="">
   </article>
</section>
```

## 1\. Sélecteur

### querySelector

Pour sélectionner une balise, on peut utiliser le querySelector en visant le nom de la balise, l'id ou la classe.

Pour mettre la section dans la variable theFirstSection, on peut utiliser :

```javascript
// avec le nom de balise
var theFirstSection=document.querySelector('section');

// avec la classe
var theFirstSection=document.querySelector('.firstSection');

// avec l'id
var theFirstSection=document.querySelector('#sectionId');

// la balise et la classe
var theFirstSection=document.querySelector('section.firstSection');

// pour sélectionner la balise img dans le .firstSection_article
var myImg=document.querySelector('.firstSection_article img');

// avec le dataset
var bouton=document.querySelector('[data-number="2"]')
```

**IMPORTANT!**

Le **querySelector** renvoie le **premier** élément qu'il trouve dans le HTML.

```javascript
var bouton=document.querySelector('button');
```

ça renvoie le **PREMIER BUTTON**

--------------------------------------------------------------------------------

### querySelectorAll

Pour sélectionner plusieurs éléments, on utilise querySelectorAll qui renvoie un **TABLEAU**

```javascript
var boutons=document.querySelectorAll('button')
```

La variable **boutons** est un **TABLEAU**. Les éléments du tableau sont utilisables avec boutons[0], boutons[1], ...

--------------------------------------------------------------------------------

## 2\. Quelques fonctions utiles

_Valeur/contenu_:

```javascript
element.innerHTML //renvoie le contenu d'une element
element.textContent //renvoie le texte d'une element
input.value //renvoie le contenu d'un input
checkbox.checked // renvoie true si la checkbox est cochée, sinon false
```

_Styles_:

```javascript
element.style.color='red'; // change le style couleur d'un element en 'red'
element.style.backgroundColor='blue'; //change le style background-color d'un element
element.style.transform='translateX(10px)';
element.style.src='img/imgopif.jpg';
element.style.display='none';
...
```

_Classes_:

```javascript
element.classList //renvoie la liste des classe d'un element
element.classList.add('nomdeclasse'); //ajoute la classe "nomdeclasse" à un élément
element.classList.remove('nomdeclasse'); //supprime la classe "nomdeclasse" à un élément
element.classList.toggle('nomdeclasse'); //ajoute la classe "nomdelaclasse" si elle est absente, supprime la classe si elle est présente
element.dataset.exemple="ex"; //Donne la valeur "ex" au "data-exemple" de la balise
```

_Tableaux_:

```javascript
var tableau=[]; // déclare un tableau
tableau.length // renvoie la taille du tableau
tableau.length-1 // indice du dernier élément du tableau
tableau.push(element); // place un "element" à la fin du "tableau"
tableau.splice(2, 3); //supprime 2 elements à partir de l'index 3 du tableau
```

Trucs:

```javascript
window.pageYOffset; //renvoie la valeur du scroll actuel de la page
```

### - Créer un élément:

```javascript
var newSpan=document.createElement('SPAN'); //Crée un élément <span></span>
newSpan.className="exempleClass" // donne la classe "exempleClass" à l'élément span
var newText=document.createTextNode('exemple'); //Crée un texte "exemple"
newSpan.appendChild(newText); //place le texte "exemple" dans l'élément span

var article=document.querySelector('.firstSection_article');
article.appendChild(newSpan); //place l'élément span dans l'aticle dans le HTML
```

### - Evenement par défaut

Pour empecher un evenement par défaut

```javascript
// empeche les evenement par defaut (le submit du formulaire par ex)
form.addEventListener('submit', function(event) {
      event.preventDefault();
});
```

## 3\. addEventListener

Pour mettre de l'intéraction, on peut placer un addEventListener sur un élément pour qu'il exécute une fonction (**function**).

```javascript
var bouton=document.querySelector('button')

var bouton.addEventListener('click', function(){
   console.log('coucou')
})
```

Lorsqu'on **clique** `'click'` sur le **premier bouton**, on affiche "coucou" dans la console.

### Des trucs :

```javascript
var window.addEventListener('keyup', function(event){
   console.log(event.which);  //renvoie le keycode de la touche du clavier qu'on relache
})
```

## 4\. Timeout, Interval

```javascript
//Affiche 'coucou' dans la console après 1000ms (1s)
var timoute = setTimeout(function () {
   console.log('coucou');  
}, 1000);

clearTimeout(timoute); //supprime le setTimeout
```

```javascript
//Affiche 'bouh' dans la console toute les 2000ms (2s)
var intervalle = setInterval(function () {
   console.log('bouh');  
}, 2000);

clearInterval(intervalle); //supprime le setInterval

```
###






### Parcel  

Pour démarrer :

Dans le terminale :

git clone le repo puis npm install dans parcel

npm start

À vous de jouer !

## Installation dépendances pour framework JS (React, Preact et VUE)

## React

/* Ajoutez un script de démarrage à package.json

package.json
"scripts": {
  "start": "parcel index.html"
}

npm install --save react
npm install --save react-dom
npm install --save-dev parcel-bundler

## Preact

npm install --save preact
npm install --save preact-compat
npm install --save-dev parcel-bundler
npm install --save-dev babel-preset-env
npm install --save-dev babel-preset-preact

# Ensuite, assurez-vous que la configuration Babel suivante est présente.

 .babelrc
{
  "presets": ["env", "preact"]
}
# Ajoutez un script de démarrage à package.json

// package.json
"scripts": {
  "start": "parcel index.html"
}

# Ajoutez un script de démarrage à package.json

 package.json
"scripts": {
  "start": "parcel index.html"
}

## VUE

npm install --save vue
npm install --save-dev parcel-bundler


/* Ajoutez un script de démarrage à package.json

 package.json
"scripts": {
  "start": "parcel index.html"
}



### Définition :

Convention : façon de faire du css avec des "règles" et des normes à suivre (nom des classes etc...)



``` javascript
document.body.insertBefore : pour déplacer un element avec le js
ex: const titre = document.getElementById("titre")
     const texte = document.body.getElementsByTagName("p")

     document.body.insertBefore(texte[1], titre)
     console.log(titre);

pour ajouter un elément a la fin : document.body.appendChild(?)
pour supprimé un elément : document.removeChild(?)

pour remplacer un elément : document.body.replaceChild(nouveauTexte, texte[1])

our genera du texte HTML en JS : function ajouterTexte(pseudo, monTexte) {

   const nouveauTexte = document.createElement('p')

   nouveauTexte.innerHTML = `<strong>${pseudo}:${monTexte}`;
   document.body.appendChild(nouveauTexte)
 }

 ajouterTexte("Antho " , " joeme")
document.body.getElementsByTagName(pour récuperé un element du dom )


POUR GENERER DU TEXTE EN JS

function ajouterTexte(monTexte) {
  const nouveauTexte = document.createElement("p")
  nouveauTexte.innerHTML = `<strong> ${monTexte}`;

  document.body.appendChild(nouveauTexte)

}
ajouterTexte("Lorem ipsum dolor sit amet");


pour récupéré et afficher un lien
const lien = document.getElementsByTagName("a")[0]
console.log(lien.getAttribute('href'));

pour modifier un lien : lien.setAttribute("href", "http://anthonywelc.com")

pour modifier un texte : const texteArray = Array.from(texte)
texteArray.map(paragraphe => paragraphe.innerHTML = "Hahahaha je t'est hacké")

pour un lien :const lien = document.body.getElementsByTagName("a")[0]
lien.setAttribute('href', "http://anthonywelc.com")


pour modifier un texte : const texteArray = Array.from(texte)
texteArray.map(paragraphe => paragraphe.innerHTML = "hahaha je t'ai hacké!")


* push(element1, …, elementN) ajoute des éléments en dernière position
* unshift(element1, …, elementN) ajoute des éléments en première position
* pop() supprime le dernier élément
* shift() supprime le premier élément
* sort() trie les éléments (par défaut dans lordre croissant)
* indexOf(element) recherche la position dun élément
* splice(start, deleteCount) supprime des éléments
* reverse() inverse lordre des éléments, le premier devenant le dernier, et ainsi de suite
* join() crée une chaîne de caractère en concaténant tous les éléments
* concat(array1, …, arrayN) 
```
