## Implémentation de tarte au citron pour le design system de l'état français

Dans l'attente du composant cookie, nous proposons une version adaptée du gestionnaire tarte au citron.

## Installation

Se référer à [la documentation officielle de tarteaucitron](https://tarteaucitron.io/fr/)

## Utilisation

[Tarte au citron sur github](https://github.com/AmauriC/tarteaucitron.js/blob/master/README.md#how-to-use)

## Utilisation du fichier css custom

Afin d'avoir les styles spécifiques au design system, vous devrez utiliser le fichier css du répertoire /css, en version normale ou minifiée. Pour cela, vous devrez changer un des paramètres d'initialisation du plugin tarteaucitron, `useExternalCss`, par défaut à `false` que vous devrez passer à `true`, comme ceci :

```
useExternalCss: true
```
À vous de choisir la manière dont vous voulez procéder pour incorporer le fichier css, vous pouvez le copier/coller dans un fichier pré-existant, ou bien l'appeler tout simplement via la balise <link>

C'est tout, les autres paramètres sont prévus pour fonctionner dans les cas prévus par le plugin.

## Pour aller plus loin
Pour des besoins éditoriaux, il est parfois nécessaire de venir changer les chaînes de caractères et/ou de rajouter des balises HTML. Ceci est possible dans les fichiers de traductions présents dans le répertoire /lang du plugin.
Par exemple, on peut vouloir venir modifier le texte du disclaimer, qui est par défaut :

> Ce site utilise des cookies et vous donne le contrôle sur ceux que vous souhaitez activer

Vous trouverez cette chaîne de caractère dans le fichier `tarteaucitron.fr.js` du répertoire lang, sa clé est `alertBigPrivacy`. Les traductions sont contenues dans un objet où vous trouverez toutes les valeurs personnalisables :
```
tarteaucitron.lang = {
    ...
    alertBigPrivacy": "vous acceptez l'utilisation de services tiers pouvant installer des cookies",
    ...
}
```

Vous pouvez à présent faire ce type de modification : 
```
tarteaucitron.lang = {
    ...
    alertBigPrivacy": "<h2>Lorem ipsum dolor sit amet</h2>" +
      "<p>Nos site et <a href>nos partenaires</a> utilisons des cookies déposés sur votre terminal avec votre consentement que vous pouvez retirer à tout moment.</p>\n" +
      "<p class='rf-text--sm'>Certains cookies sont dits fonctionnels et sont strictement necessaires à la bonne fourniture du service. Ils peuvent comprendrent des traceurs de mesure d’audience motorant le bon fonctionnement technique du site." +
      "Des cookies dits ‘non fonctionnels’ peuvent être déposés, permettant de personnaliser des contenus selon votre navigation, d’afficher de la publicité personnalisée ou non, géolocalisée ou non en se basant sur votre profil et/ou historique de navigation.</p>",
    ...
}
```
