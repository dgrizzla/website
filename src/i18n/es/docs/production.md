# ✨ Producción

Cuando llega el momento empaquetar su aplicación para producción, se puede usar el modo de producción de Parcel.

```bash
parcel build entry.js
```

Esto deshabilita el modo de observación y _hot module replacement_ para que se construya una única vez. También se habilita el minificador para todas las salidas empaquetadas, reduciendo el tamaño del archivo. Los minificadores usados por Parcel son [uglify-es](https://github.com/mishoo/UglifyJS2/tree/harmony) para JavaScript, [cssnano](http://cssnano.co) para CSS, y [htmlnano](https://github.com/posthtml/htmlnano) para HTML.

Habilitando el modo de producción también asigna la variable de entorno `NODE_ENV=production`. Librerías grandes como React tienen caracteristicas de _debugging_ solo para desarrollo, quedando deshabilitadas al asignar esta variable de entorno, lo que resulta en construcciones más pequeñas y rápidas para producción.


### Opciones

#### Asignar el directorio de salida

Por defecto: "dist"

```bash
parcel build entry.js --out-dir build/output
o
parcel build entry.js -d build/output
```

```base
root
- build
- - output
- - - entry.js
```

#### Asignar el URL público para servir la aplicación

Por defecto: --out-dir option

```bash
parcel build entry.js --public-url ./
```

Produce:

```html
<link rel="stylesheet" type="text/css" href="1a2b3c4d.css">
o
<script src="e5f6g7h8.js"></script>
```


#### Deshabilitar la minificación

POr defecto: La minificación está habilitada

```
parcel build entry.js --no-minify
```

#### Deshabilitar el cache en el sistema de archivos
Por defecto: El cache está habilitado

```bash
parcel build entry.js --no-cache
```
