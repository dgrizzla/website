# 📝 Tipo de Assets

Como se describe en la [documentación de los assets](assets.html), Parcel representa cada archivo como un `Asset`. Los tipos de Assets son representados como clases heredadas de la clase base `Asset` e implementando la interface requerida para interpretar, analizar dependencias, transformar y generar código.

Debido a que parcel procesa los assets en paralelo a través de múltiples núcleos, las transformaciones que pueden hacer los tipos de assets son limitados a esos que operan en un solo archivo a la vez. Para las transformaciones a través de múltiples archivos, un [Packager](packagers.html) personalizado puede ser usado.

## Interface de Asset

```javascript
const {Asset} = require('parcel-bundler');

class MyAsset extends Asset {
  type = 'foo'; // define el tipo de salida principal

  parse(code) {
    // interpreta el codigo a un AST
    return ast;
  }

  pretransform() {
    // transformarcion opcional antes de recolectar las dependencias
  }

  collectDependencies() {
    // analizar dependencias
    this.addDependency('my-dep');
  }

  transform() {
    // transformarcion opcional antes de recollectar las dependencias
  }

  generate() {
    // generar codigo. puedes retornar multiples interpretaciones si es necesario
    // los resultado son pasado al packagers apropiado para generar el paquete final.
    return {
      foo: 'my stuff here', // salida principal
      js: 'some javascript' // interpretacion alternativa para ser colocada en el paquete de JS si es necesario
    };
  }
}
```

## Registrando un Tipo de Asset

Puedes registrar tu tipo de asset con un empaquetador usando el metodo `addAssetType`. Acepta una extension de archivo para registrar y un path a tu modulo. Es un path en vez de un objeto para que se pueda ser pasado al los worker processes

```javascript
const Bundler = require('parcel-bundler');

let bundler = new Bundler('input.js');
bundler.addAssetType('.ext', require.resolve('./MyAsset'));
```
