# my-nth-test-app

## Project setup
```
npm install
npm run serve
# in another terminal, in the project folder
node server.js
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
    data: {
      sivousavezdeschamps: 'rentrez les ici'
    }
  })
  .then((response) => {
    console.log('response', response)
  })
```

