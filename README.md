# Site vitrine — mode d'emploi

`index.html` est un site complet en **un seul fichier** (HTML/CSS/JS, aucune dépendance). Ouvre-le dans un navigateur pour le voir.

## 1. Personnaliser
Cherche et remplace dans `index.html` :
- `[votre téléphone]` et le lien `tel:+33000000000`
- Les cartes de la section **Réalisations** (mets tes vraies démos + captures du dossier `04_`)
- Les liens **Mentions légales / Confidentialité** du pied de page (utilise `06_Admin-Compta/mentions-legales-site.md`)
- Le nom `Mohamed.dev` si tu veux un autre logo

## 2. Brancher le formulaire sur n8n (ton atout démo)
Le formulaire envoie un POST JSON vers un **webhook n8n**. Étapes :

1. Dans n8n, crée un workflow avec un nœud **Webhook** (méthode `POST`, chemin ex. `/contact`).
2. Copie l'URL de production du webhook.
3. Dans `index.html`, remplace la constante :
   ```js
   const N8N_WEBHOOK_URL = "https://VOTRE-INSTANCE-N8N/webhook/contact";
   ```
4. Ajoute à la suite du webhook, dans n8n, par exemple :
   - un nœud **Email / Gmail** → tu reçois la demande instantanément ;
   - un nœud **Google Sheets / base** → la demande alimente ton CRM (`liste-cibles.csv`) ;
   - une **réponse auto** au prospect (« merci, je vous réponds vite »).

Données envoyées : `nom, entreprise, email, telephone, besoin, message, date, source`.

> ⚠️ CORS : autorise l'origine de ton site dans le nœud Webhook (paramètre *Response* / *Allowed Origins*) si le navigateur bloque la requête. Alternative sans n8n immédiat : un service type Formspree, puis migrer vers n8n.

## 3. Mettre en ligne (gratuit)
- **GitHub Pages** : pousse `index.html` dans un repo → Settings → Pages → déployer. (Tu connais déjà GitHub Actions, tu peux automatiser.)
- **Netlify / Cloudflare Pages** : glisse le dossier, c'est en ligne en 1 min.
- **Nom de domaine** : achète `ton-nom.fr` et pointe-le dessus. Pour tes clients, rappelle-toi : domaine **au nom du client** (voir `01_Offres-Tarifs/regles-hebergement.md`).

## 4. Plus tard : version Angular ?
Tu es à l'aise en Angular 19 — tu pourras porter cette page en composant Angular si tu veux un blog ou un back-office. Mais pour une vitrine, ce fichier statique est plus rapide, plus léger et parfait pour le SEO. Ne complique pas au départ.
# MN2A
