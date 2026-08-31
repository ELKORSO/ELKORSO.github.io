# Déployer votre site sur GitHub Pages

Ce dossier contient un site statique prêt à l'emploi (`index.html` + fichiers annexes). Pas de build, pas de framework : tout se modifie directement dans `index.html` avec un éditeur de texte.

## 1. Créer le dépôt GitHub

1. Connectez-vous sur [github.com](https://github.com).
2. Cliquez sur **New repository** (bouton vert, en haut à droite).
3. Nommez le dépôt **exactement** `VOTRE-NOM-UTILISATEUR.github.io` (remplacez par votre pseudo GitHub réel — c'est ce nom précis qui active l'hébergement gratuit à la racine, comme pour `gulvarol.github.io`).
4. Laissez-le **Public**, ne cochez aucune case d'initialisation (pas de README auto), puis **Create repository**.

## 2. Envoyer les fichiers

**Option A — depuis le site GitHub (le plus simple, sans ligne de commande) :**
1. Sur la page du nouveau dépôt, cliquez sur *uploading an existing file*.
2. Glissez-déposez tous les fichiers de ce dossier (`index.html`, `robots.txt`, `sitemap.xml`, `.nojekyll`, le dossier `assets/`).
3. *Commit changes*.

**Option B — avec Git en ligne de commande :**
```bash
cd chemin/vers/ce/dossier
git init
git add .
git commit -m "Site initial"
git branch -M main
git remote add origin https://github.com/VOTRE-NOM-UTILISATEUR/VOTRE-NOM-UTILISATEUR.github.io.git
git push -u origin main
```

## 3. Activer GitHub Pages

1. Dans le dépôt : **Settings → Pages**.
2. *Source* : `Deploy from a branch` → branche `main`, dossier `/ (root)` → **Save**.
3. Pour un dépôt nommé `VOTRE-NOM-UTILISATEUR.github.io`, la publication est en général automatique.
4. Après 1 à 2 minutes, votre site est en ligne à :
   `https://VOTRE-NOM-UTILISATEUR.github.io/`

## 4. Personnaliser les liens avant la mise en ligne définitive

Dans `index.html`, remplacez les 3 occurrences de `VOTRE-USERNAME.github.io` (balise `<link rel="canonical">`, le champ `"url"` des données structurées JSON-LD, et dans `og:image` si besoin) par votre véritable adresse. Faites de même dans `robots.txt` et `sitemap.xml`.

## 5. Nom de domaine personnalisé (optionnel mais recommandé)

Pour une adresse comme `www.votrenom.fr` ou `votrenom.com` :
1. Achetez le domaine chez un registrar (OVH, Gandi, Namecheap…).
2. Chez le registrar, créez un enregistrement DNS de type `CNAME` pointant `www` vers `VOTRE-NOM-UTILISATEUR.github.io`.
3. Dans **Settings → Pages** du dépôt, champ *Custom domain*, entrez votre domaine et cochez *Enforce HTTPS*.
4. GitHub crée automatiquement un fichier `CNAME` dans le dépôt — ne le supprimez pas.

---

# Remplacer l'ancien site (Google Sites) sans perdre votre référencement

Votre ancienne page (`sites.google.com/site/nabkorso`) est indexée par Google, donc la transition demande quelques actions — Google Sites ne permet pas de redirection HTTP automatique (pas de code 301), il faut donc "rediriger" les visiteurs et les moteurs de recherche manuellement.

**1. Ne supprimez pas l'ancienne page tout de suite.** Modifiez plutôt son contenu : remplacez le texte par un message court et un lien bien visible, par exemple :

> *« Ce site a déménagé. Retrouvez ma page à jour ici : [nouvelle adresse] »*

Une page vide de contenu mais avec un lien clair est bien plus utile qu'une page supprimée (erreur 404), aussi bien pour vos visiteurs que pour Google, le temps que l'indexation se mette à jour.

**2. Déclarez le nouveau site dans Google Search Console.**
1. Allez sur [search.google.com/search-console](https://search.google.com/search-console).
2. Ajoutez une propriété avec votre nouvelle URL (`https://VOTRE-NOM-UTILISATEUR.github.io/`).
3. Vérifiez la propriété (méthode "balise HTML" : Google vous donne une balise `<meta>` à coller dans le `<head>` de `index.html`, ou méthode "fichier HTML" à déposer à la racine).
4. Une fois vérifié, onglet **Sitemaps** → soumettez `sitemap.xml`.
5. Onglet **Inspection de l'URL** → collez l'URL de la page d'accueil → **Demander une indexation**.

**3. Mettez à jour tous les liens qui pointent vers l'ancien site** — c'est ce qui compte le plus pour transférer votre "autorité" Google, bien plus que la page elle-même :
- Le champ "Homepage" de votre profil **Google Scholar**.
- Votre page **DBLP** (un correctif peut être demandé via leur formulaire).
- Votre page personnelle sur le site du **laboratoire L2S / CentraleSupélec**.
- **LinkedIn**, ResearchGate, ORCID, et toute signature d'e-mail ou CV en PDF.
- Les pages de vos co-auteurs ou de votre université qui vous citent.

**4. Patience.** Un site neuf met généralement de quelques jours à quelques semaines pour bien se positionner sur votre nom. Le fait que l'ancien site pointe vers le nouveau, et que Search Console ait indexé le nouveau, accélère nettement le transfert.

---

# Modifier le contenu du site

Tout le contenu est écrit en clair dans `index.html`, avec des commentaires en français qui indiquent où et comment ajouter un élément (une actualité, une publication, un rôle éditorial…). Ouvrez le fichier avec n'importe quel éditeur de texte (VS Code, Bloc-notes, TextEdit), repérez la section à modifier grâce aux commentaires `<!-- ... -->`, copiez un bloc existant (par exemple une publication) et modifiez le texte. Enregistrez, puis renvoyez le fichier sur GitHub (Option A ou B ci-dessus) — le site se met à jour automatiquement en une minute ou deux.
