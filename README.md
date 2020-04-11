# my-nth-test-app

## MISE EN PROD

Allez regarder le fichier [mise-en-prod.md](mise-en-prod.md) pour les détails concernant la mise en prod

## Gestion des sessions lors du développement

Pour des raisons de sécurité, par défaut, les cookies ne sont pas transmis pour les
requêtes de type CORS. Pour que ceux-ci fonctionnent dans votre projet, vérifiez que vous
avez bien deux éléments dans votre projet:

Fichier src/main.js (regardez l'exemple dans le fichier de ce projet):
```js
// cette ligne est importante pour les sessions (en mode développement)
axios.defaults.withCredentials = true
```

Fichier server.js (en remplacement de `app.use(cors())`, déplacé au dessus de
`app.use(session({`, regardez l'exemple dans le fichier de ce projet)
```js
// ces lignes (cors) sont importantes pour les sessions dans la version de développement
app.use(cors({
  credentials: true,
  origin: 'http://localhost:8080' // si votre port est différent, changez cette valeur !
}))
```

## Project setup
```
npm install
npm install --save express express-session body-parser morgan cors
npm install -g nodemon # (auto restart the server)
npm run serve
# in another terminal, in the project folder
nodemon server.js
```

installer Axios sur votre projet:
```
npm install --save axios vue-axios
```
Ensuite ajoutez les lignes suivantes à votre fichier src/main.js:
(regardez l'exemple dans le fichier correspondant de ce projet)
```
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)
```

Ensuite, depuis n'importe quel composant (regardez l'exemple dans
src/components/HelloWorld.vue):
```
  this.axios.post('https://localhost:4000/votreAPI', {
    sivousavezdeschamps: 'rentrez les ici'
  })
  .then((response) => {
    console.log('response', response)
  })
```
test
test2
