# crudEasy
Easily creates CRUD operations through browseable HTML routes and RESTful API json routes, in Node.js with ExpressJS and MongoDB

_Requires Node.js, MongoDB and Express_

# Installation instructions
1. download repository
2. rename _config-template.js_ to _config.js_ and change accordingly, to setup your MongoDB user, password, collection and URL, and to insert your OAuth keys (such as Facebook, Twitter, Google+ and LinkedIn)
3. go to the directory _crudEasy_ and run _npm install_
4. require crudEasy with the options set forth below.
5. Do so for as many routes and collections as needed!

## v. 0.1
- First version. just basic CRUD oeprations and full views and RESTful API functions

## Documentation

### Observations

- Throughout the code, ":modelModule" is used in comments as an alias to the name given when the module was instantiated, but there is no such param in the routes.
- Options are passed through as a parameters object, and all of its contents are required, otherwise there will be missing routes and variables. However, error handling of undefined hasn't been implemented yet.


### Basic initialization

:modelModule
options = {
    collection:     "processos",
    defaultPerPage: 10,
    routeNew:       "/novo",
    routeDelete:    "/:item/excluir",
    routeEdit:      "/:item/editar",
    labelNew:       "Novo",
    labelEdit:      "Editar",
    viewNew:        "processos/form.jade",
    viewItem:       "processos/view.jade",
    viewList:       "processos/list.jade",
    viewEdit:       "processos/form.jade",
}

First instantiate a new model by calling `var modelInstance = new crudEasy.newModel(url, collectionName);` and then use the api and crud routes by calling ` app.use([route], crudEasy.crudRoute(modelInstance, optionsObject));`  and `app.use([/api/route],crudEasy.apiRoute(modelInstance, optionsObject));`

```javascript
crudEasy = {
    newModel:   function(url, collectionName){return require('lib/_objectMongodb')(url, collectionName);},
    crudRoute:  function(url, collectionName){return require('lib/crud')();}
}
```

## Contact

Feel free to contact me on `renatoxsr[at]gmail.com`.

From São Paulo, Brazil.

Happy coding!
