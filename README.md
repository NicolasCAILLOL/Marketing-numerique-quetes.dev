# Marketing-numérique-quetes.dev

# Quête 1 : Comment fonctionne un moteur de recherche ?

Exercice pratique : vérifier si le contenu principal d'une page est présent dans le **HTML brut** reçu du serveur, ou s'il n'apparaît qu'après **exécution du JavaScript**.

## Site testé

- **URL** : https://www.ynov.com/
- **Requête** : `GET`, statut `200 OK`

## Méthode

1. Ouverture des outils de développement de Chrome (`F12`), onglet **Network**.
2. Rechargement de la page avec le filtre **Doc**.
3. Affichage du **code source brut** (clic droit → « Afficher le code source de la page », ou `Ctrl+U`). Ce code est le HTML tel que le serveur l'envoie, avant toute exécution de JavaScript.
4. Recherche (`Ctrl+F`) de textes visibles sur la page pour vérifier s'ils sont présents dans ce code source.
5. Comparaison avec l'onglet **Elements** de l'inspecteur, qui montre le DOM après exécution du JS.

## Question

Le contenu principal de la page est-il déjà présent dans le code source brut, ou apparaît-il seulement après exécution du JavaScript ?

## Réponse

**Le contenu principal est déjà présent dans le code source brut.**

Le site ynov.com est **rendu côté serveur (SSR)** : le HTML arrive complet dans la réponse du serveur. Googlebot peut donc crawler et indexer la page **sans avoir besoin d'exécuter de JavaScript**.

## Preuves relevées dans le code source brut

| Élément | Exemple trouvé dans le HTML brut |
|---|---|
| Balise `<title>` | `École supérieure de formation aux métiers du digital - Ynov` |
| Balise `meta description` | Présente dans le `<head>` |
| Titres `<h2>` | « L'école des transformations digitales », « 3 Pôles d'excellence », « Ynov en quelques chiffres », « FAQ » |
| Texte | Paragraphes de présentation, chiffres clés (« 14 campus », « 9 000 étudiants ») |
| Liens crawlables | De nombreux `<a href="https://www.ynov.com/formations/...">` en clair |
| Images | Attributs `alt` présents (ex. « Capgemini partenaire Ynov Campus ») |
| Données structurées | Deux blocs `application/ld+json` : `Organization` et `FAQPage` |
| Indexation | `<meta name="robots" content="index, follow, ...">` |
| Canonical | `<link rel="canonical" href="https://www.ynov.com/">` |

## Lien avec les 3 étapes d'un moteur de recherche

- **Crawl** : les liens `<a href>` sont dans le HTML initial, le crawler peut les suivre dès le téléchargement de la page.
- **Indexation** : titres, texte et attributs `alt` sont lisibles directement. La page est explicitement autorisée à être indexée (`index, follow`).
- **Ranking** : une page bien indexée peut ensuite être classée sur la pertinence de son contenu.

## Conclusion

Sur https://www.ynov.com/, le contenu principal (titres, textes, liens, balises meta, données structurées) est déjà dans le HTML brut. Le rendu est côté serveur, donc la page est directement exploitable par un moteur de recherche sans exécution de JavaScript.
