# 🍰 Recetas

## React

Primero se deben instalar las dependencias para React.

[Blog Post](http://blog.jakoblind.no/react-parcel/). _En Ingles_

```
npm install --save react
npm install --save react-dom
npm install --save-dev parcel-bundler
npm install --save-dev babel-preset-env
npm install --save-dev babel-preset-react
```

<sub>O utilizando el gestor de paquetes opcional Yarn</sub>

```
yarn add react
yarn add react-dom
yarn add --dev parcel-bundler
yarn add --dev babel-preset-env
yarn add --dev babel-preset-react
```


Luego debe asegurarse que se encuentre la siguiente configuración de Babel.

```javascript
 // .babelrc
{
  "presets": ["env", "react"]
}
```

Agregar el script _Start_ a `package.json`

```javascript
// package.json
"scripts": {
  "start": "parcel index.html"
}
```

## Preact

Primero se debe instalar las dependencias para Preact.

```
npm install --save preact
npm install --save preact-compat
npm install --save-dev parcel-bundler
npm install --save-dev babel-preset-env
npm install --save-dev babel-preset-preact
```

<sub>O utilizando el gestor de paquetes opcional Yarn</sub>

```
yarn add preact
yarn add preact-compat
yarn add --dev parcel-bundler
yarn add --dev babel-preset-env
yarn add --dev babel-preset-preact
```

Luego debe asegurarse que se encuentre la siguiente configuración de Babel.

```javascript
// .babelrc
{
  "presets": ["env", "preact"]
}
```

Agregar el script _Start_ a `package.json`

```javascript
// package.json
"scripts": {
  "start": "parcel index.html"
}
```
