## Implémentation de tarte au citron pour le DSFR

Dans l'attente du composant cookie, nous proposons une version adaptée du gestionnaire tarte au citron.

## Installation

Se référer à [la documentation officielle de tarteaucitron](https://tarteaucitron.io/fr/)

## Utilisation

[Tarte au citron sur github](https://github.com/AmauriC/tarteaucitron.js/blob/master/README.md#how-to-use)



## Utilisation du fichier css custom

Afin d'avoir les styles spécifiques au design system, vous devrez utiliser le fichier css de ce répertoire, en version normale ou minifiée. Pour cela, vous devrez changer un des paramètres d'initialisation du plugin tarteaucitron, `useExternalCss`, par défaut à `false` que vous devrez passer à `true`, comme ceci :

```
useExternalCss: true
```
Vous pouvez désormais utiliser le fichier `tac.custom.css` ou `tac.custom.min.css` en l'incorporant dans la section <head> de votre site :
```html
<head>
    <link rel="stylesheet" href="path/to/tac-custom.css">
</head
```
Vous pouvez également copier/coller le code contenu dans le fichier pour le mettre dans un fichier css pré-existant ou l'importer dans un préprocesseur type sass si vous souhaitez éviter un appel css supplémentaire. À vous de voir !

Voilà, c'est tout !

## Exemple de configuration

Voici notre configuration d'initialisation pour l'exemple :
```html
<script type="text/javascript">
    tarteaucitron.init({
        /* General */
        "privacyUrl": "",                /* Privacy policy url . Si vide, le lien Politique de confidencialité du bandeau ne s'affiche pas*/
        "hashtag": "#consentement",      /* La gestionnaire de consentement s'ouvre avec ce hashtag lorsqu'il est placé dans l'url */
        "cookieName": "tarteaucitron",   /* L'identifiant du cookie déposé sur le poste utilisateur */
        "bodyPosition": "top",           /* Position à laquelle le gestionnaire - niveau 2 -  est inséré dans la page (top ou bottom). Pour que les technologies d'assistance puisse y acceder rapidement à la navigation, 'top' est la valeur privilégiée. */
        "adblocker": false,              /* Show a Warning if an adblocker is detected */
        "highPrivacy": true,             /* Retire le consentement implicite (au scroll ou à la navigation) Activé par défaut, donc on peut le retirer de cette config */
        "handleBrowserDNTRequest": false,/* Active ou désactive la prise en compte du Do Not track Navigateur. Si le DNT est activé, aucun cookie n'est déposé */
        "useExternalCss": true,         /* Active ou non une css custom - désactive ou non la css par défaut */
       
        /* Bandeau d'information cookies (niveau 1)*/
        "orientation": "bottom",/* Position de la bannière de niveau 1 (middle - top - bottom). Si la position est middle, il y a un overlay derrière donc laisser à top ou bottom. */
        "DenyAllCta" : true,    /* Affiche le bouton 'Tout refuser' sur le bandeau de niveau 1 */
        "AcceptAllCta" : true,  /* Affiche le bouton 'Tout accepter' sur le bandeau de niveau 1 */
        "closePopup": false,    /* ajoute une croix de fermeture */

        /* Gestionnaire de cookies (niveau 2) */
        "removeCredit": true, /* Affiche ou non les credit TAC */
        "moreInfoLink": true,/*  Affiche ou non le liens vers les infos*/
        "readmoreLink": true,/* Change the default readmore link pointing to tarteaucitron.io */
        "mandatory": true,    /* Message à propos des cookies dits fonctionnels  */


        /* Sticky d'ouverture niveau 2 */
        /* Blocs 'Gestion des cookies' */
        "showAlertSmall": false, /* 'bouton' sticky (en bas a droite) permettant d'ouvrir le gestionnaire de niveau 2*/
        "cookieslist": false,   /* Ajoute le nombre de services au 'block' sticky */
        /* Icone sticky */
        "showIcon": false,             /* affichage du Bouton sticky (icone citron) pour ouvrir le gestionnaire */
        "iconPosition": "BottomLeft", /* Position du Bouton sticky BottomRight, BottomLeft, TopRight and TopLeft */
        "groupServices": false
    });
</script>
```

## Modifier les chaînes de caractère (sans back-office)

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
## Modifier les chaînes de caractère (avec back-office)

Dans le back-office de tarteaucitron, vous avez accès aux chaînes de caractères directement dans l'interface.
Dans l'onglet "Mes Sites", cliquer sur le lien "Modifier le texte" dans la section "Configuration" du tableau. 

![Image](../main/img/accueil.png?raw=true)

Choisisser ensuite la langue concernée, par exemple "Français (fr)" puis changer le texte avec ou sans balises au niveau de la chaîne de caractères que vous souhaitez modifier, dans le champs "Description".

![Image](../main/img/configuration.png?raw=true)
