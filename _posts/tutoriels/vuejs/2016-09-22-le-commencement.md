---
layout: post
title: Le commencement
description: Découverte du framework VueJS
author: alex
logo: https://cdn.auth0.com/blog/vuejs/vue-logo.png
categories:
  - tutoriels
  - vuejs
---
C'est parti, vous avez décidé de vous mettre à `vue.js`, ou vous êtes juste curieux d'en savoir plus, ça tombe bien, je vais tenter de vous expliquer ce que c'est et comment l'utiliser rapidement !

### Qu'est-ce Vue.js ?

Vue.js est une librairie JavaScript créé par [Evan You](https://github.com/yyx990803) et permet de créer des applications web facilement.

Site internet officiel : [http://vuejs.org/](http://vuejs.org/)

Vue.js se veut simple d'utilisation et rapide à prendre en main, pour cela, rien de mieux qu'un exemple !

### Installation (Basique)

Comme toute librairie JS, on va l'intégrer dans notre code HTML avec la balise `<script>` (dans le header ou footer, ça c'est vous qui décidez !) :

```html
<script type="text/javascript" src="http://cdnjs.cloudflare.com/ajax/libs/vue/1.0.26/vue.min.js"></script>
```

Pour cet exemple, on va utiliser la version 1 de Vue.js et la récupérer directement via [https://cdnjs.com/](https://cdnjs.com/)

```html
<div id="demo">
  {% raw %}<p>{{ message }}</p>{% endraw %}
  <input v-model="message">
</div>
```

```js
new Vue({
  el: '#demo',
  data: {
    message: 'Bienvenue sur Atinux.fr !'
  }
});
```


Résultat *(modifiez la valeur de l'input afin de modifier la phrase affichée en direct)* :
<div id="demo" style="border: 1px solid #ddd; padding: 10px;margin-bottom: 15px;">
{% raw %}
  <p style="margin:0;">{{ message }}</p>
{% endraw %}
  <input v-model="message" style="padding: 5px;">
</div>

<script type="text/javascript">
new Vue({
  el: '#demo',
  data: {
    message: 'Bienvenue sur Atinux.fr !'
  }
});
</script>

Essayons maintenant de voir ce qu'il se passe côté HTML :

```html
<div id="demo">...</div>
```
* On créé une `<div>` et on lui assigne l'id `demo`, cela nous permettra de connecter notre vue avec l'élément HTML pour le rendre dynamique.

```html
{% raw %}<p>{{ message }}</p>{% endraw %}
```
* Dans notre `<p>` on ajoute `{% raw %}{{ message }}{% endraw %}`, cela affichera le contenu de notre variable `message` (en échappant les caractères HTML)

```html
<input v-model="message">
```
* On ajoute un attribut spécial de Vue.js nommé `v-model` qui va écouter sur les changements de notre `<input>` et modifier directement le contenu de la variable `message`

Côté JavaScript nous avons plusieurs choses :

```js
new Vue({
  // ...
});
```
* La création de notre première vue avec Vue.js, pour ceci, on l'instancie en appelant : `new Vue()`

```js
new Vue({
  el: '#demo',
  // ...
})
```
* Nous précisons à Vue.js d'utiliser notre elément HTML `#demo` afin de le rendre dynamique, il va s'en servir comme template pour y remplacer nos `{% raw %}{{ message }}{% endraw %}` par son contenu mais aussi rendre dynamique notre `<input>` car il reconnait l'attribut `v-model` propre à Vue.js

```js
new Vue({
  // ...
  data: {
    message: 'Bienvenue sur Atinux.fr !'
  }
})
```
* Dans `data`, on rajoute la variable `message` que l'on va utiliser dans notre HTML, celui-ci sera automatiquement modifié à chaque fois que l'on va modifier la valeur de notre `<input>`

C'est là où intervient toute la magie de Vue.js ! Il va automatiquement écouter sur les changements du formulaire, modifier la variable `message` et répercuter les modifications directement où la variable `message` est affiché, ici dans notre `<p>`.
