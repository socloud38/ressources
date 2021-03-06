<div align="center">
  <h1>
    <span>Women on Rails</span><br/>
    <span>Le site des ressources</span>
  </h1>

  <img src="website/static/img/favicon.ico">
  
  ---

  Un site pour définir ensemble des **ressources** pour recherche d'emploi, préparation d'entretiens, formations, veille...<br>
  Un **blog** pour partager ses connaissances tech et ses retours d'expériences.</br><br/>
  Dernière mise à jour: octobre 2020<br/>
  Créé en utilisant [Docusaurus](https://docusaurus.io/).<br/>
  
  https://women-on-rails.github.io/ressources/

  ---
</div><br/><br/>

**Sommaire du README**
- [Installer le site en local](#installer-le-site-en-local)
- [Structure du dossier website](#structure-du-dossier-website)
- [Comment modifier du contenu](#comment-modifier-du-contenu)
  - [Comment éditer une page doc existante](#comment-éditer-une-page-doc-existante)
  - [Comment éditer un article de blog existant](#comment-éditer-un-article-de-blog-existant)
- [Comment ajouter du contenu](#comment-ajouter-du-contenu)
  - [Ajouter une nouvelle page doc](#ajouter-une-nouvelle-page-doc)
  - [Ajouter un nouvel article de blog](#ajouter-un-nouvel-article-de-blog)
  - [Ajouter des éléments à la barre de navigation du haut](#ajouter-des-éléments-à-la-barre-de-navigation-du-haut)
  - [Ajouter une page custom](#ajouter-une-page-custom)
- [La documentation officielle](#la-documentation-officielle)
- [Comment soumettre ton code](#comment-soumettre-ton-code)
- [Idées de pages à écrire](#idées-de-pages-à-écrire)

# Installer le site en local
1. Vérifie que tu as [node](https://nodejs.org/en/download/) insallé et [yarn](https://classic.yarnpkg.com/fr/docs/install/#mac-stable).

2. Clone le repo

3. Installe les dépendances:

```sh
$ yarn
```

4. Lance le serveur local:

```sh
$ yarn start
```

Cela va t'ouvrir une page `http://localhost:3000/`

# Structure du dossier website

Tu trouves dans `website/blog` les articles et dans `website/docs` les pages du site dans des sous-dossiers.<br/>
Les fichiers images sont dans `website/src/assets/img` et tu peux ajouter du css custom dans `website/src/assets/css/custom.css`.<br/>
La barre de navigation sur le côté est dans le fichier `website/src/sidebar.js`.

```
website/
  docs/
    dossier/
      doc-1.md
      doc-2.md
      doc-3.md
  website/
    blog/
      2016-3-11-oldest-post.md
      2017-10-24-newest-post.md
    core/
    node_modules/
    pages/
    src/
      assets/
        css/
        img/
      sidebars.js
    package.json
    docusaurus.config.js
```

# Comment modifier du contenu

## Comment éditer une page doc existante

Tu peux modifier une page en te rendant dans le dossier `website/docs` et en modifiant le document que tu veux:
`website/docs/document-a-modifier.md`


```markdown
---
id: document-à-modifier
title: Document à modifier
---

À modifier...
```

[Pour plus d'information sur les docs](https://docusaurus.io/docs/en/navigation).

## Comment éditer un article de blog existant

Tu peux modifier une page en te rendant dans le dossier `website/blog` et en modifiant l'article que tu veux:
`website/blog/article-a-modifier.md`

```markdown
---
id: article-a-modifier
title: Article à modifier
---

À modifier...
```

[Pour plus d'information sur les articles de blog](https://docusaurus.io/docs/en/adding-blog).

# Comment ajouter du contenu

## Ajouter une nouvelle page doc

1. Ajoute un nouveau document au format markdown dans le dossier `website/docs`, comme par exemple `website/docs/nouveau-doc.md`:

```md
---
id: nouveau-doc
title: Nouveau doc
---

Nouveau contenu.
Nouvelle vie.
```

2. Rajoute l'ID de ce doc dans le fichier de la barre de navigation: `website/src/sidebars.js`:

```javascript
{
  "docs": {
    "Bienvenue": [
      "start",
      "nouveau-doc" // ajoute ton doc ici
    ],
    ...
  },
  ...
}
```

3. Tu peux soit l'ajouter directement dans une catégorie existante (ici: `Bienvenue`) soit créer ta propre catégorie sous le format:

```javascript
{
  "docs": {
    "Nouvelle catégorie": [
      "nouveau-doc"
    ],
    ...
  },
  ...
}
```

[Pour plus d'information sur comment ajouter un doc](https://docusaurus.io/docs/en/navigation).

## Ajouter un nouvel article de blog

Ajoute un article avec le format `YYYY-MM-DD-Le-Titre-De-Mon-Article.md` dans `website/blog`:

`website/blog/2020-10-03-It-s-October-Third.md`

```markdown
---
author: Foo Bar
authorURL: https://twitter.com/foobarbaz
authorFBID: 503283835
title: It's October Third
---

Lorem Ipsum...
```

L'aperçu de l'article doit se situer au-dessus de la ligne `truncate`

```markdown
// Haut de l'article
  <!--truncate-->
// Suite de l'article
```

[Pour plus d'information sur comment ajouter un article](https://docusaurus.io/docs/en/adding-blog).

## Ajouter des éléments à la barre de navigation du haut

Tu peux ajouter des liens vers les documents, des pages customs ou vers des sites externes en modifiant la clé `headerLinks` du fichier `website/docusaurus.config.js`

`website/docusaurus.config.js`

```javascript
{
  headerLinks: [
    ...
    /* ajouter un doc */
    { doc: 'exemples', label: 'Exemples' },
    /* ajouter une page custom */
    { page: 'Aide', label: 'Aide' },
    /* ajouter un site externe */
    { href: 'https://github.com/facebook/docusaurus', label: 'GitHub' },
    ...
  ],
  ...
}
```

[Pour plus d'information sur la barre de navigation du haut](https://docusaurus.io/docs/en/navigation).

## Ajouter une page custom

Docusaurus utilise les React components pour construire des pages. Les pages sont sauvegardés au format .js dans `website/src/pages`

[Pour plus d'information sur les pages custom](https://docusaurus.io/docs/en/custom-pages).

# La documentation officielle

Docusaurus a une [documentation très détaillée](https://v2.docusaurus.io/docs/2.0.0-alpha.65/) pour tout ce qui est création de page, ajout de style... N'hésite pas à t'y référer, en particulier la section [Guides](https://v2.docusaurus.io/docs/2.0.0-alpha.65/creating-pages).<br/>
Pour le style des pages custom, Docusaurus utilise [Infima](https://facebookincubator.github.io/infima/docs/getting-started/introduction).

# Comment soumettre ton code
**À partir du site**: cliquer sur le lien "Edit this page" en bas d'une des pages ressources, forker le repo puis commiter ton changement et faire une Pull Request.<br/>
**Sur GitHub**: forker le repo, faire les changements en ligne nécessaires:
- modifier un fichier en cliquant sur le petit crayon en haut
<img src="website/static/img/edit_file.png">
- ajouter un fichier
<img src="website/static/img/create_file.png">

**En local**: forker puis cloner le repo, faire une nouvelle branche, commiter tes changements puis pusher. Revenir sur la page de ce repo et soumettre ta Pull Request.<br/>

# Idées de pages à écrire
- Ajouter une catégorie **Apprendre** avec les pages: 
  - pourquoi apprendre à coder
  - pourquoi choisir Ruby on Rails
  - comment se former (sites, formation...)
- Dans la catégorie **Trouver un job**
  - ajouter les pages suivantes:
    - candidater (rédiger un CV / une lettre de motivation)
    - le processus d'embauche (le déroulé du process: appel / test technique / retours, ce qu'attend les recruteurs d'un entretien / test)
    - les questions à poser lors du recrutement
    - après l'entretien (comment remercier / relancer)
   - ajouter sur la page "Questions techniques" directement des questions en Ruby, Rails, SQL, Active Records, par niveau
- Dans la catégorie **Pratiquer**:
  - rajouter une présentation de l'open source / petite historique sur la page concernée
  - rajouter dans la page projets persos des exemples de projets sous RoR
- Dans la catégorie **Rejoindre la communauté**:
  - Faire une page "Transmettre" avec: Écrire des articles (medium, dev.io); Rejoindre des réseaux solidaires (social builder); Participer à un talk (comment se préparer) => Tout ça peut éventuellement être une catégorie en soi
- Ajouter une catégorie **Visualuser l'écosystème RoR**:
  - Trombinoscope avec profils twitter (DHH, Matz...)
  - Recenser les entreprises qui codent en RoR par localisation avec des liens vers leurs pages présentant leur tech, leur équipe...
- Ajouter une catégorie **S'inspirer**:
  - Page "Portraits de développeuses"
- Ajouter une catégorie **Au-delà de RoR**:
  - Page "Les petits plus en entreprise" avec des ressources pour: command line, git, regex, sql, css / html, bootstrap, vanilla JS, comment se débugguer
  - Ressources Front-End
  - Resources Design
  - Ressources Computer Science
- Ajouter une catégorie **Lexique** ?
  - Page  "Termes techniques du site" ?
  - Page "Jargon start-up" ?
