# 🔌 Plugins

Parcel difiere de otras herramientas en la forma en que muchos formatos comunes son incluidos sin la necesidad de instalar o configurar _plugins_ adicionales. Sin embargo, existen casos en los que usted quisiera extender Parcel en formas no-estándar, para estos casos, los _plugins_ son soportados. Los _plugins_ instalados son automáticamente detectados y cargados según las dependencias en `package.json`.

Cuando se agrega soporte para un nuevo formato de archivo en Parcel, se debe considerar inicialmente que tan adoptado se encuentra el formato, y que tan estandarizada es su implementación. Si es suficientemente adoptado y estandarizado, el formato probablemente debería ser agregado al núcleo de Parcel y no implementado como un plugin que los usuarios deban instalar. Si se tienen dudas, [GitHub](https://github.com/parcel-bundler/parcel/issues) es el lugar correcto para discutirlas.

## API de Plugins

Los plugins en Parcel son muy simples. Son nada más módulos que exportan una sola función, que es llamada por Parcel automáticamente durante la inicialización. La función recibe como entrada el objeto `Bundler`, y puede realizar configuraciones tales como registrar tipos de recursos(_asseets_) y empaquetadores(_packagers_).

```javascript
module.exports = function (bundler) {
  bundler.addAssetType('ext', require.resolve('./MiRecurso'));
  bundler.addPackager('foo', require.resolve('./MiEmpaquetador'));
};
```

Publique este paquete en npm usando el prefijo `parcel-plugin-`, y será automáticamente detectado y cargado como se describe a continuación.

## Usando Plugins

No podría ser más fácil usar _plugins_ en Parcel. Todo lo que se debe hacer es instalar y guardar el _plugin_ en el `package.json`. Los _plugins_ deben ser nombrados usando el prefijo `parcel-plugin-`, e.g. `parcel-plugin-foo`. Cualquier dependencia ubicada en `packages.json` con este prefijo va a ser automáticamente cargada durante la inicialización.
