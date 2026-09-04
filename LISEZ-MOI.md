# Structure à pousser dans le repo GitHub

Le repo `marco-ares/Quiz-coupleinc` doit contenir exactement ceci à sa racine :

```
wrangler.jsonc
public/
  index.html
  sombre.html
```

Rien d'autre. Pas de fichier HTML à la racine.

## Pourquoi

Cloudflare a créé un projet **Workers**, pas un projet **Pages**. Le Workers exécute
`npx wrangler deploy`, et wrangler cherche un dossier de fichiers statiques. Il ne le
trouvait pas, parce que le HTML était à la racine et qu'aucun `wrangler.jsonc` ne lui
disait où regarder.

Le `wrangler.jsonc` règle ça : il nomme le projet et pointe vers `./public/`.

## Après le push

Cloudflare redéploie automatiquement. Les deux adresses :

- `https://quiz-coupleinc.[ton-sous-domaine].workers.dev` : version claire
- `https://quiz-coupleinc.[ton-sous-domaine].workers.dev/sombre` : version sombre

Si le déploiement échoue encore, vérifier dans Settings que la **Deploy command** est bien
`npx wrangler deploy` et que le **Root directory** est `/`.
