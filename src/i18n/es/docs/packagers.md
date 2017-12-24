# 📦 EMpaquetadores

En Parcel, un `Packager`(Empaquetador) combina distintos `Asset`s(Recursos) en un único paquete de salida. Esto sucede en el proceso principal después de haber procesado todos los recursos y haber creado un árbol(colección ordenada de los recursos) del paquete.  Los empaquetadores son registrados según el tipo de salida, y los recursos que han generado ese tipo de salida son enviados al empaquetador para la producción del archivo final de salida.

## Interfaz de empaquetadores

```javascript
const {Packager} = require('parcel-bundler');

class MiEmpaquetador extends Packager {
  async start() {
    // opcional. escribir el encabezado del archivo si es necesario.
    await this.dest.write(header);
  }

  async addAsset(recurso) {
    // requerido. escribir el recurso en el archivo de salida.
    await this.dest.write(recurso.generated.foo);
  }

  async end() {
    // opcional. escribir el trailer del archivo si es necesario.
    await this.dest.end(trailer);
  }
}
```

## Registrando un Empaquetador

Se puede registrar un Empaquetador(_pakager_) con un _bundler_ usando el método `addPackager`. Como parámetros acepta el tipo de archivo a registrar, y la ruta al módulo del empaquetador.

```javascript
const Bundler = require('parcel-bundler');

let bundler = new Bundler('input.js');
bundler.addPackager('foo', require.resolve('./MiEmpaquetador'));
```
