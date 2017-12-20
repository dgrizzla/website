# 🐠 Transformaciones

Mientras que muchos empaquetadores requieren la instalación y configurción de los _plugins_ para transformar los recursos, Parcel cuenta con soporte para múltiples transformadores y transpiladores comúnmente utilizados. Puede transformar JavaScript usando [Babel](https://babeljs.io), CSS usando [PostCSS](http://postcss.org), y HTML usando [PostHTML](https://github.com/posthtml/posthtml).

Esto funciona inclusive en `node_modules` de terceros: si se cuenta con un archivo de configuración provisto por el paquete, la transformación es habilitada automáticamente para este módulo únicamente. Esto mantiene el empaquetamiento rápido, dado que solo los módulos que requieren ser transformados son procesados. Esto también significa que no debe configurar las transformaciones manualmente para incluir ciertos archivos, ni conocer como el código del tercero es construido para ser utilizado en su aplicación.

## Babel

[Babel](https://babeljs.io) es un transpilador popular para JavaScript, con un gran ecosistema de plugins. Utilizar Babel con Parcel funciona de la misma manera que utilizándolo solo o con otros empaquetadores.

Instalar _presets_ y _plugins_ en su aplicación:

```bash
yarn add babel-preset-env
```

Luego, crear un archivo `.babelrc`:

```json
{
  "presets": ["env"]
}
```

## PostCSS

[PostCSS](http://postcss.org) es una herramienta para transformar CSS con _plugins_, como, [autoprefixer](https://github.com/postcss/autoprefixer), [cssnext](http://cssnext.io/), y [CSS Modules](https://github.com/css-modules/css-modules). Puede configurar PostCSS con Parcel creando un archivo de configuración con alguno de los siguientes nombres: `.postcssrc` (JSON), `.postcssrc.js`, o `postcss.config.js`.

Instalar los _plugins_ en su aplicación:

```bash
yarn add postcss-modules autoprefixer
```

Luego, crear un archivo `.postcssrc`:

```json
{
  "modules": true,
  "plugins": {
    "autoprefixer": {
      "grid": true
    }
  }
}
```

Los _plugins_ son especificados como llaves en el objeto `plugins`, y se definen las opciones utilizando valores para los objetos. Si no existen opciones para un plugin, nada más asignelo a `true`.

En el archivo `.browserslistrc` se puede especificar los navegadores destino para Autoprefixer, cssnext y otras herramientas:

```
> 1%
last 2 versions
```

Los CSS Modules son habilitados de manera similar usando la llave de nivel superior `modules`. Esto dado que Parcel necesita tener soporte espcial para CSS Modules puesto que CSS Modules exporta un objeto que se incluye en el empaquetado también. Note que aún asi debe instalar `postcss-modules` en su proyecto.

## PostHTML

[PostHTML](https://github.com/posthtml/posthtml) es una herramienta para transformar HTML con _plugins_. Puede configurar PostHTML con Parcel creado un archivo de configuración con alguno de los siguientes nombres: `.posthtmlrc` (JSON), `posthtmlrc.js`, or `posthtml.config.js`.

Instalar _plugins_ en su aplicación:

```bash
yarn add posthtml-img-autosize
```

Luego, crear un archivo `.posthtmlrc`:

```json
{
  "plugins": {
    "posthtml-img-autosize": {
      "root": "./images"
    }
  }
}
```

Los _plugins_ son especificados como llaves en el objeto `plugins`, y las opciones son definidas usando valores para los objetos. Si no hay opciones para un _plugin_, nada más asignelo a `true`.
