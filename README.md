# Mon suivi — déploiement Vercel

Ce dossier contient une application web statique (pas de build, pas de dépendances) :

```
vercel-app/
├── index.html      ← toute l'application (HTML + CSS + JS)
└── vercel.json     ← config pour éviter les soucis de cache sur Safari
```

## Déployer (sans rien installer)

1. Va sur https://vercel.com et connecte-toi (ou crée un compte gratuit).
2. Clique **Add New… → Project**.
3. Choisis **"Deploy without Git"** / glisse-dépose directement le dossier `vercel-app` (celui qui contient `index.html`).
4. Laisse les réglages par défaut (aucun framework détecté, c'est normal, c'est un site statique) et clique **Deploy**.
5. Au bout de quelques secondes, Vercel te donne une URL du type `https://mon-suivi.vercel.app`.

## Déployer avec la ligne de commande (si tu préfères)

```bash
npm install -g vercel
cd vercel-app
vercel        # déploiement de test
vercel --prod # déploiement définitif
```

## Installer sur l'iPhone comme une app

1. Ouvre l'URL Vercel dans **Safari** sur l'iPhone (pas Chrome — l'ajout à l'écran d'accueil en mode plein écran ne fonctionne qu'avec Safari sur iOS).
2. Bouton de partage (le carré avec la flèche) → **"Sur l'écran d'accueil"**.
3. Une icône apparaît, elle s'ouvre en plein écran, sans barre d'adresse.

## Où sont stockées les données ?

Les données (poids, pas, calories, prénom) sont enregistrées directement dans le navigateur de l'iPhone (stockage local du site). Elles restent donc sur cet appareil et ne sont jamais envoyées à un serveur. Si elle change de téléphone ou vide les données de Safari, l'historique sera perdu — il n'y a pas encore de sauvegarde dans le cloud.

## À savoir : les vibrations

J'ai ajouté le code pour déclencher une vibration à chaque validation (`navigator.vibrate`). C'est une limitation d'Apple, pas de l'app : **Safari sur iPhone ne permet pas aux sites web de déclencher le moteur de vibration**, même installés sur l'écran d'accueil. Cette fonctionnalité ne marchera donc pas sur iPhone tant qu'Apple ne change pas cette règle. Le code est prêt si elle utilise un jour l'app sur Android (Chrome), où ça fonctionne. Sur iPhone, le bouton garde un petit effet d'enfoncement au tap pour donner un retour visuel à la place.
