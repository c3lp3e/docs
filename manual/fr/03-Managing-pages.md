# Gestion des pages

Les chapitres suivants expliquent comment gérer les pages de Contao. Depuis que Contao est un système de gestion de contenu basé sur les pages, ces dernières et la structure du site sont les éléments centraux de votre site internet et tout contenu qui n'est pas associé à une page ne ​​pourra jamais être vu.

## Composants

Comprendre comment les pages, les articles, les éléments de contenu et les modules sont liés entre eux est la clé de l'apprentissage de Contao. Comme mentionné précédemment, la structure du site est l'élément central de votre site. Les visiteurs de votre site internet demandent toujours des pages et non des articles comme dans un CMS basé sur des nœuds.

![](https://raw.github.com/contao/docs/3.1/manual/en/images/components.jpg)

Le diagramme montre que les articles et les présentations de page sont les deux éléments les plus importantes d'une page. Alors que les articles stockent le contenu d'une page, la présentation de page définit la façon dont il est affiché sur le site. Les présentations de page de Contao sont basé sur les CSS et bien sûr elles n'utilisent pas de mise en page avec des tables. Les chapitres suivants expliquent comment créer des feuilles de style et des modules, comment les combiner dans une présentation de page et comment créer des pages qui l'utilisent.

## Thèmes

Bien que le gestionnaire de thème est une nouvelle fonctionnalité de la version 2.9, il est en fait juste une interface améliorée pour quelque chose qui faisait déjà partie de Contao. Une design de site internet se compose généralement de feuilles de style, de modules front office, de présentations de page, de fichiers et de modèles que vous pouvez gérer dans le back office de Contao. Le gestionnaire de thème ne change pas cette approche du tout, il ajoute juste une option pour exporter et importer ces ressources.


### Thèmes par opposition aux modèles du front office

La principale différence entre les [thèmes][1] et les modèles du front office est qu'un modèle du front office contient un exemple de site internet entièrement préconfiguré, y compris un exemple de structure du site, d'articles, d'éléments de contenu et même d'utilisateurs et de groupes d'utilisateurs. Un thème, en revanche, ne contient que le design du site internet et peut donc être importé sans risque de perdre toutes les données existantes.

![](https://raw.github.com/contao/docs/3.1/manual/en/images/theme-manager.jpg)


### Composants d'un thème

Un thème est un groupe de [feuilles de style][2], de [modules front office][3] et de [présentations de page][4], qui sont tous stockés dans la base de données et automatiquement reconnu par l'exportateur de thème. Vous en apprendrez plus sur ces éléments dans les chapitres suivants. Un thème inclut habituellement des images et d'autres fichiers à partir du répertoire des fichiers et des modèles personnalisés en option à partir du répertoire des modèles. Toutefois, ces ressources ne sont pas automatiquement liées avec le thème et doivent donc être ajoutées dans la configuration du thème pour y être inclues dans l'exportation.

![](https://raw.github.com/contao/docs/3.1/manual/en/images/theme-settings.jpg)


### Exportation et importation d'un thème

Pour exporter un thème, cliquez simplement sur le bouton d'exportation et télécharger le fichier .cto en local sur votre ordinateur. Bien que .cto est une extension de fichier propriétaire pour les thèmes de Contao, le fichier est en fait une archive ZIP qui peut être extraite avec chaque programme qui traite les fichiers .zip. Pour réimporter un thème, téléversez le fichier .cto dans votre installation Contao, ouvrez le gestionnaire de thèmes et cliquez sur "Import de thème". Vous pouvez importer plusieurs thèmes à la fois. Une fois l'importation terminée, vous pouvez affecter une ou plusieurs présentations de page du nouveau thème dans la structure du site.


## Feuilles de style

Les sites internet accessibles doivent toujours être formatés à l'aide des CSS, c'est pourquoi Contao inclut un module "feuilles de style" qui vous permet de gérer les définitions de formatage dans le back office. Pour référencer les différents éléments de Contao, vous devez connaître leurs noms de classe. Les [classes des éléments de contenu][5] commencent par "ce\_" (par exemple "ce_text") et les [classes des modules][3] avec "mod\_" (par exemple "mod_search"). Si vous n'êtes pas sûr, il suffit de regarder dans le code source de la page.

![](https://raw.github.com/contao/docs/3.1/manual/en/images/style-sheet.jpg)

Chaque feuille de style peut être limitée par un ou plusieurs types de média et/ou par une version particulière d'Internet Explorer, dans le cas où vous avez besoin de fixer un de ses nombreux bogues. Faites attention à l'ordre des définitions de formatage, car celles qui suivent, remplacent les précédentes.

``` {.css}
/* Définir la valeur générale d'abord */
.mod_search {
    margin:24px;
}

/* Puis la remplacer pour IE7 */
*:first-child+html .mod_search {
    margin:18px;
}
```

Si l'ordre est inversé, la valeur générale l'emporterait sur la marge spécifique
à Internet Explorer.


## Modules

Front end modules allow you to add almost any kind of functionality to your
website. The Contao core includes modules to generate various navigation menus,
handle user registration and authentication, search the website, import RSS
feeds and many more. To create a module, log into the back end and choose
"Themes" -> "Front end modules" in the navigation menu.

<table>
<tr>
  <th>Module</th>
  <th>Classe CSS</th>
  <th>Description</th>
</tr>
<tr>
  <td>Menu de navigation</td>
  <td>mod_navigation</td>
  <td>Génère un menu de navigation à partir de la structure du site.</td>
</tr>
<tr>
  <td>Navigation personnalisée</td>
  <td>mod_customnav</td>
  <td>Génère un menu personnalisé.</td>
</tr>
<tr>
  <td>Navigation "fil d'Ariane"</td>
  <td>mod_breadcrumb</td>
  <td>Génère un menu de type "fil d'Ariane".</td>
</tr>
<tr>
  <td>Navigation rapide</td>
  <td>mod_quicknav</td>
  <td>Génère un menu de type liste déroulante à partir de la structure du site.</td>
</tr>
<tr>
  <td>Lien rapide</td>
  <td>mod_quicklink</td>
  <td>Génère un menu de type liste déroulante.</td>
</tr>
<tr>
  <td>Navigation "Livre"</td>
  <td>mod_booknav</td>
  <td>Génère un menu de type "Livre".</td>
</tr>
<tr>
  <td>Pagination d'articles</td>
  <td>mod_article_nav</td>
  <td>Génère une pagination pour naviguer dans les articles.</td>
</tr>
<tr>
  <td>Plan du site</td>
  <td>mod_sitemap</td>
  <td>Génère une liste de toutes les pages de la structure du site.</td>
</tr>
<tr>
  <td>Formulaire de connexion</td>
  <td>mod_login</td>
  <td>Génère un formulaire de connexion.</td>
</tr>
<tr>
  <td>Déconnexion automatique</td>
  <td>-</td>
  <td>Déconnecte automatiquement un membre.</td>
</tr>
<tr>
  <td>Données personnelles</td>
  <td>mod_personalData</td>
  <td>Génère un formulaire permettant de modifier les données personnelles d'un membre.</td>
</tr>
<tr>
  <td>Formulaire d'inscription</td>
  <td>mod_registration</td>
  <td>Crée un formulaire d'inscription.</td>
</tr>
<tr>
  <td>Mot de passe perdu</td>
  <td>mod_password</td>
  <td>Crée un formulaire de demande de nouveau mot de passe.</td>
</tr>
<tr>
  <td>Fermer le compte</td>
  <td>mod_closeAccount</td>
  <td>Crée un formulaire pour supprimer le compte d'un membre.</td>
</tr>
<tr>
  <td>Liste d'actualités</td>
  <td>mod_newslist</td>
  <td>Ajoute une liste d'actualités à la page.</td>
</tr>
<tr>
  <td>Lecteur d'actualités</td>
  <td>mod_newsreader</td>
  <td>Affiche les détails d'une actualité.</td>
</tr>
<tr>
  <td>Archive d'actualités</td>
  <td>mod_newsarchive</td>
  <td>Ajoute une archive d'actualités à la page.</td>
</tr>
<tr>
  <td>Menu archive d'actualités</td>
  <td>mod_newsmenu</td>
  <td>Génère un menu de navigation pour une archive d'actualités.</td>
</tr>
<tr>
  <td>Calendrier</td>
  <td>mod_calendar</td>
  <td>Ajoute un calendrier dans une page.</td>
</tr>
<tr>
  <td>Lecteur d'événement</td>
  <td>mod_eventreader</td>
  <td>Affiche les détails d'un événement.</td>
</tr>
<tr>
  <td>Liste d'événements</td>
  <td>mod_eventlist</td>
  <td>Ajoute une liste d'événements dans une page.</td>
</tr>
<tr>
  <td>Menu liste d'événements</td>
  <td>mod_eventmenu</td>
  <td>Génère un menu de navigation pour parcourir la liste d'événements.</td>
</tr>
<tr>
  <td>S'abonner</td>
  <td>mod_subscribe</td>
  <td>Génère un formulaire pour s'abonner à une ou plusieurs listes de diffusion.</td>
</tr>
<tr>
  <td>Se désabonner</td>
  <td>mod_unsubscribe</td>
  <td>Génère un formulaire pour se désabonner à une ou plusieurs listes de diffusion.</td>
</tr>
<tr>
  <td>Liste de bulletins d'information</td>
  <td>mod_nl_list</td>
  <td>Ajoute une liste de bulletins d'information à une page.</td>
</tr>
<tr>
  <td>Lecteur de bulletins d'information</td>
  <td>mod_nl_reader</td>
  <td>Affiche les détails d'un bulletin d'information.</td>
</tr>
<tr>
  <td>Liste de FAQ</td>
  <td>mod_faqlist</td>
  <td>Ajoute une liste de questions fréquemment posées dans la page.</td>
</tr>
<tr>
  <td>Lecteur de FAQ</td>
  <td>mod_faqreader</td>
  <td>Affiche la réponse à une question fréquemment posée.</td>
</tr>
<tr>
  <td>Page de FAQ</td>
  <td>mod_faqpage</td>
  <td>Afficher la liste de FAQ et le lecteur de FAQ sur la même page.</td>
</tr>
<tr>
  <td>Formulaire</td>
  <td>mod_form</td>
  <td>Ajoute un formulaire dans la page.</td>
</tr>
<tr>
  <td>Moteur de recherche</td>
  <td>mod_search</td>
  <td>Ajoute un formulaire de recherche dans la page.</td>
</tr>
<tr>
  <td>Commentaires</td>
  <td>mod_comments</td>
  <td>Gérer les commentaires ou les entrées d'un livre d'or.</td>
</tr>
<tr>
  <td>Liste d'enregistrements</td>
  <td>mod_listing</td>
  <td>Lister les enregistrements d'une table de la base de données.</td>
</tr>
<tr>
  <td>Animation Flash</td>
  <td>mod_flash</td>
  <td>Permet d'inclure une animation Flash dans une page.</td>
</tr>
<tr>
  <td>Liste d'articles</td>
  <td>mod_article_list</td>
  <td>Génère une liste d'articles contenu dans une zone particulière.</td>
</tr>
<tr>
  <td>Image aléatoire</td>
  <td>mod_random_image</td>
  <td>Ajoute une image aléatoire dans une page.</td>
</tr>
<tr>
  <td>Code HTML personnalisé</td>
  <td>-</td>
  <td>Permet d'inclure du code HTML personnalisé.</td>
</tr>
<tr>
  <td>Lecteur de flux RSS</td>
  <td>mod_rss_reader</td>
  <td>Ajoute un flux RSS à la page.</td>
</tr>
</table>


### Access control

Each front end module can be protected so only guests or members of a particular
group can see it on the website.

![](https://raw.github.com/contao/docs/3.1/manual/en/images/protected-module.jpg)


## Page layouts

Page layouts determine the basic page setup, e.g. the number of columns or the
overall width, and they define which front end modules are shown in which
columns. They also allow you to include style sheets, to link to RSS or Atom
feeds, to associate a Google Analytics ID and to add arbitrary JavaScript code
that is required to control interactive elements and plugins. The Contao CSS
framework automatically divides the browser window into several layout sections
and shows the modules that have been assigned to them one below the other.

![](https://raw.github.com/contao/docs/3.1/manual/en/images/front-end-structure.jpg)

![](https://raw.github.com/contao/docs/3.1/manual/en/images/front-end-modules.jpg)

That implies that by the time you create a page layout, you have to have created
all style sheets and front end modules that you want to include in it. Therefore
it is recommended to create resources in the following order:

* Create the necessary front end modules
* Create the necessary style sheets
* Optionally create news archives or calendars
* Create a new page layout and combine the components


## Page types

The page type determines whether a page shows content, forwards to another page
or defines the starting point of a new website within the page tree. Contao
supports 6 different page types which are explained below.

<table>
<tr>
  <th>Page type</th>
  <th>Description</th>
</tr>
<tr>
  <td>Regular page</td>
  <td>A regular page contains articles and content elements. It behaves like a
      static HTML page.</td>
</tr>
<tr>
  <td>External redirect</td>
  <td>This type of page automatically redirects visitors to an external website.
      It works like a hyperlink.</td>
</tr>
<tr>
  <td>Internal redirect</td>
  <td>This type of page automatically forwards visitors to another page within
      the site structure.</td>
</tr>
<tr>
  <td>Website root</td>
  <td>This type of page marks the starting point of a new website within the
      site structure.</td>
</tr>
<tr>
  <td>403 Access denied</td>
  <td>If a user requests a protected page without permission, a 403 error page
      will be loaded instead. This page must be added <b>on the first level</b> inside your website root page.</td>
</tr>
<tr>
  <td>404 Page not found</td>
  <td>If a user requests a non-existent page, a 404 error page will be loaded
      instead. This page must be added <b>on the first level</b> inside your website root page.</td>
</tr>
</table>


### Multi-domain mode

Contao supports multiple websites within the site structure and automatically
redirects visitors to a particular website root page depending on its DNS and
language settings. Let us assume that you are running a bilingual corporate
website which uses the domain "www.company.com" and a small private website
which uses the domain "www.personal-website.com". You need three website root
pages for that:

<table>
<tr>
  <th>Type</th>
  <th>DNS</th>
  <th>Language code</th>
  <th>Fallback language</th>
</tr>
<tr>
  <td>German corporate website</td>
  <td>none</td>
  <td>de</td>
  <td>no</td>
</tr>
<tr>
  <td>English corporate website</td>
  <td>none</td>
  <td>en</td>
  <td>yes</td>
</tr>
<tr>
  <td>Personal website</td>
  <td>personal-website.com</td>
  <td>de</td>
  <td>yes</td>
</tr>
</table>

The following table shows to which page a visitor will be redirected depending
on the domain and his browser language.

<table>
<tr>
  <th>Domaine</th>
  <th>Langue du navigateur</th>
  <th>Cible de redirection</th>
</tr>
<tr>
  <td>www.company.com</td>
  <td>Anglais</td>
  <td>Site internet d'entreprise en Anglais</td>
</tr>
<tr>
  <td>www.company.com</td>
  <td>Allemand</td>
  <td>Site internet d'entreprise en Allemand</td>
</tr>
<tr>
  <td>www.company.com</td>
  <td>Espagnol</td>
  <td>Site internet d'entreprise en Espagnol</td>
</tr>
<tr>
  <td>www.personal-website.com</td>
  <td>Non pertinent</td>
  <td>Site internet personnel</td>
</tr>
</table>

Note that if we had not set the "language fallback" option, the personal website
would only be available for German speaking users!


### Droits d'accès

Les droits d'accès déterminent ce que les utilisateurs du back office sont autorisés à faire avec une page et ses articles. Ils n'ont rien à voir avec les pages protégées qui ne sont accessibles que par certains utilisateurs front office ! Similaire au système de permissions des fichiers Unix, il existe trois niveaux d'autorisation :

* Accès en tant que propriétaire d'une page
* Accès en tant que membre d'un groupe propriétaire de la page
* Accès en tant qu'utilisateur sans privilège

Each level can have different permissions. By default, the owner of a page is
allowed to edit the page itself as well as its articles, whereas a member of the
group that owns a page is only allowed to edit articles. Unprivileged users have
no writing permissions at all.

![](https://raw.github.com/contao/docs/3.1/manual/en/images/access-rights.jpg)


[1]: https://contao.org/en/contao-themes-and-templates.html
[2]: 03-Managing-pages.md#style-sheets
[3]: 03-Managing-pages.md#modules
[4]: 03-Managing-pages.md#page-layouts
[5]: 04-Managing-content.md#articles