# Documentation

## Convention BEM

```html

<!--- maintList = block -->
<ul class="mainList mainList--xmas">

    <!--__list = Element -->
    <li class="mainList__item">

        <!-- __itemLink = Elemnt -->    
        <a class="mainList__itemLink mainList__itemLink--isActive" href="/home">Accueil</a>

    </li>

    <!--__list = Element -->
    <li class="mainList__item">

        <!-- __itemLink = Elemnt -->
        <a class="mainList__itemLink" href="/home">Accueil</a>

    </li>

    <!--__list = Element -->
     <li class="mainList__item">

    <!-- __itemLink = Elemnt -->
    <a class="mainList__itemLink" href="/home">Accueil</a>

    </li>

</ul>

```

```css
.mainList {
    display: flex;
    justify-content: space-between;
        &--xmax{
            background: green;
        }
        &__item {
            list-style: none;
        }
        &__itemLink {
            color:red;
            &--isActive{
                color: white;
            }
        }
    }

```

## Pseudo attributs

Les Pseudo attrbuts 'befor' et 'after' permettent de créer des noeuds HTML et CSS.
Ils sont essentiellement utilisés pour ajouter des ornements, des décorations ... On peut bien entendu faire des animations avec, les positions par rapport à leur parent (relative / absolute).
* Ils doivent obligatoirement avoir un 'content:
* fin de s'afficher.

```html
<section class="cover">
    <h1 class ="cover__mainTitle">Présentation des pseudo-attributs</h1>
</section>
```

```css
.cover{
background: #FDFDFD;
padding: 20px;
&__mainTitle {
    text-align: center;
    font-size: 24px;
    color: green;
    position: relative
    &::before,
    &::after {
        position: absolute
        content: '';
        display : block;
        width : 50px;
        height: 50px;
        background : green;
        }
        &::before{
            left: 0;
        }
        &::after{
            right: 0;
        }
    }  
}
``
#REM, EM, %, VW sizing

#EM

```css
.cover{
    font-size: 100%;
&__mainTitle
    {
    font-size: .8em;
    }
}
````

### REM
*le REM est basé sur la taille de la racine (soit la balsie html) qui, par défaut a une valeur de 16 px. Afin d'éviter tout calcul, il est nécessaire de l'écraser en donnant une base de 10px soit 62,5%. Le REM est intéressant à utiliser si les media-queries emplayées sont en rem également. Cela vous permettre de garder des proportions égales lorsqu'on va redimensionner la page. Ses proportions seront également gardées quand l'utilisateur zoomera dans votre page.*

## vw

*Unités relatives à la taille de votre écran (peu importe le device)
Attention au VH et à son contenu. 100vh === 100vh quoi qu'il arrive.
VW : trés utiles pour les interfaces fluides.*


## flexboxgrid

*Les modificateurs réactifs permettent de spécifier différentes tailles de colonnes, décalages, alignement et distribution aux largeurs de la fenêtre xs, sm, md & lg*

  ``HTML
  <div class="row">
      <div class="col-xs-12
                  col-sm-8
                  col-md-6
                  col-lg-4">
          <div class="box">Responsive</div>
      </div>
  </div>
```

```css
    voir flexboxgrid.min.css
```

https://github.com/h5bp/Front-end-Developer-Interview-Questions


### Parcel

Starter David : https://github.com/davidvenin/parcel-starter


#### Simple "Hello World"

index.html => 

```html
<html>
<body>
  <script src="./index.js"></script>
</body>
</html>
```

index.js =>

```js
// import d'un autre composant
import main from './main';

main();
```

main.js =>   

```js
// import d'un module CSS
import classes from './main.css';

export default () => {
  console.log(classes.main);
};
```

main.js =>   

```css
.main {
  /* Référence à un fichier image */
  background: url('./images/background.png');
  color: red;
}
```

Il suffit maintenant d'executer la commande parcel index.html pour démarrer le serveur de dev.


### Webpack

Fichier de configuration basique webpack.config.js => 

```js
const path = require('path');

module.exports = {
  entry: './path/to/my/entry/file.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js'
  }
};
```

### React context API

https://reactjs.org/docs/context.html

Basic example with a provider and a consumer => 

```js
// Context lets us pass a value deep into the component tree
// without explicitly threading it through every component.
// Create a context for the current theme (with "light" as the default).
const ThemeContext = React.createContext('light');

class App extends React.Component {
  render() {
    // Use a Provider to pass the current theme to the tree below.
    // Any component can read it, no matter how deep it is.
    // In this example, we're passing "dark" as the current value.
    return (
      <ThemeContext.Provider value="dark">
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
}

// A component in the middle doesn't have to
// pass the theme down explicitly anymore.
function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton(props) {
  // Use a Consumer to read the current theme context.
  // React will find the closest theme Provider above and use its value.
  // In this example, the current theme is "dark".
  return (
    <ThemeContext.Consumer>
      {theme => <Button {...props} theme={theme} />}
    </ThemeContext.Consumer>
  );
}
```

### Redux

​- Actions​ => https://redux.js.org/basics/actions    

Actions are payloads of information that send data from your application to your store. They are the only source of information for the store. You send them to the store using store.dispatch().

​- Reducers​ => https://redux.js.org/basics/reducers  

Reducers specify how the application's state changes in response to actions sent to the store. Remember that actions only describe what happened, but don't describe how the application's state changes.

​- Store​ => https://redux.js.org/basics/store    

The Store is the object that brings them together.

## React Suspense

[Medium Article about React Suspense](https://medium.com/@baphemot/understanding-react-suspense-1c73b4b0b1e6)

## Just a little bit of golang
