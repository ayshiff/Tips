# Documentation

## BEM convention

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

Pseudo attrbuts 'befor' and 'after' allow you to create HTML and CSS nodes.
They are basically used to add ornaments, decorations.
* They must obligatorily have a 'content

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
* The REM is based on the size of the root (ie the html tag) which, by default, has a value of 16 px. To avoid any calculation, it is necessary to crush it by giving a base of 10px or 62.5%. The REM is interesting to use if the used media-queries are in rem as well. This will allow you to keep equal proportions when resizing the page. Its proportions will also be kept when the user zooms in your page. *

## vw

* Units related to the size of your screen (no matter the device)
Watch out for the VH and its contents. 100vh === 100vh whatever happens.
VW: very useful for fluid interfaces. *


## flexboxgrid

* Reactive modifiers allow you to specify different column sizes, offsets, alignment, and distribution at window widths xs, sm, md & lg *

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
    see flexboxgrid.min.css
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

You just have to run the parcel index.html command to start the dev server.


### Webpack

Basic configuration file webpack.config.js => 

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

# setState() in componentWillMount()

Avoid async initialization in ``componentWillMount()``

``componentWillMount()`` is invoked immediately before mounting occurs.
It is called before ``render()``, therefore setting state in this method will not trigger a re-render.
Avoid introducing any side-effects or subscriptions in this method.


Make async calls for component initialization in ``componentDidMount`` instead of ``componentWillMount``
```javascript
function componentDidMount() {
  axios.get(`api/messages`)
    .then((result) => {
      const messages = result.data
      console.log("COMPONENT WILL Mount messages : ", messages);
      this.setState({
        messages: [...messages.content]
      })
    })
}
```

## Apollo client example

```js
import React from 'react';
import { render } from 'react-dom';
import ApolloClient from 'apollo-boost';
import { ApolloProvider } from 'react-apollo';

// Pass your GraphQL endpoint to uri
const client = new ApolloClient({ uri: 'https://nx9zvp49q7.lp.gql.zone/graphql' });

const ApolloApp = () => (
  <ApolloProvider client={client}>
    <App />
  </ApolloProvider>
);

render(ApolloApp, document.getElementById('root'));
```

Let's create our `<App />` component and make our first query:

```js
import React from 'react';
import { gql } from 'apollo-boost';
import { Query } from 'react-apollo';

const GET_DOG = gql`
  query {
    dog(breed: "bulldog") {
      id
      breed
      displayImage
    }
  }
`

const App = () => (
  <Query query={GET_DOG}>
    {({ loading, error, data }) => {
      if (loading) return <div>Loading...</div>;
      if (error) return <div>Error :(</div>;

      return (
        <Dog url={data.dog.displayImage} breed={data.dog.breed} />
      )
    }}
  </Query>
)
```

## Just a little bit of golang

Simple test pointers :

```go
func add (a *int8) int8 {
	*a++
	return *a
}

func main () {
    var test int8 = 0
    var pointer = &test
	add(pointer)
	fmt.Println(test)
}

```

