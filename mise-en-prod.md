1) Modifier server.js et ajouter les deux lignes suivantes après app.use(cors()):
```js
const path = require('path')
app.use(express.static(path.join(__dirname, 'dist/')))
```

2) enlever toute référence à http://localhost:4000 dans vos fichiers .vue
   => http://localhost:4000/api/login devient simplement /api/login

4) dans le fichier .gitignore, retirez la ligne /dist, puis
```sh
git add .gitignore
git commit -m "remove /dist"
```

3) dans le dossier du projet à chaque nouvelle version, lancez la commande
```js
npm run build
git add ./dist
git commit -m "add new version"
```
   => cette commande doit être tapée à chaque nouvelle version de votre code

4) Dans votre fichier package.json, après la ligne `"lint": "vue-cli-service lint"`,
ajoutez la ligne suivante:
```js
"start": "node server.js"
```
n'oubliez pas de mettre une virgule à la fin de la ligne précédente

4) Allez sur glitch.com
5)   > New Project > Clone from git repo
6)   > Cliquez sur "show" en haut à gauche
7)   > Attendez jusqu'à ce que ça fonctionne
Pour débugger les problèmes, vous pouvez visualiser les logs dans "Tools" > Logs
