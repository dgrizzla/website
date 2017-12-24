# 🛠 Como Funciona

Parcel transforma un árbol de **recursos**(_assets_) a un árbol de **bundles**. Muchos otros _bundlers_ están hechos fundamentalmente para recursos de JavaScript, con otros formatos incluidos - e.g. agregados como cadenas en los archivos JS. Parceles agnóstico en cuanto al tipo de archivo - funciona con cualquier tipo de recurso en la manera que se espera, sin configuración. Hay tres pasos en el proceso de construcción con Parcel.

### 1. Construyendo el Árbol de Recursos

Parcel toma como entrada un único recurso, que puede ser de cualquier tipo: un archivo JS, HTML, CSS, imagen, etc. Existen varios [tipos de recursos](asset_types.html) definidos en Parcel que saben como manejar tipos de archivo específicos. Los recursos son analizados, sus dependencias extraidas, y son transformados a su forma final compilada.. Esto crea el árbol de recursos.

### 2. Construyendo el Árbol del _Bundle_

Una vez que se ha construido el árbol de recursos, los reecursos son colocados en un árbol de _bundle_. Un _bundle_ es creado para el recurso de entrada, y _bundles_ hijos son creados para los `import()` dinámicos, que causan que la separación del código ocurra. 

_Bundles_ hermanos son creados cuando los recursos de distintos tipos son importados, por ejemplo si se importa un archivo CSS desde Javascript, sería colocado en un _bundle_ hermano al JavaScript correspondiente.

Si un recurso es requerido en más de un _bundle_, es elevado al ancestro más cercano en el árbol de _bundle_ para no ser incluido más de una vez.

### 3. Empaquetamiento

Luego de haber construido el _bundle_, cada _bundle_ es escrito a un archivo por un [empaquetador](packagers.html) específico a este tipo de archivo. Los empaquetadores saben como combinar el código de cada recurso en un solo archivo final que es cargado por el navegador.
