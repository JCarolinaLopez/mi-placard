# Mi Placard

App instalable (PWA) para elegir qué ponerse para la oficina, llevar el inventario
de ropa por temporada y armar cápsulas para viajes de trabajo. Funciona offline y
guarda todo en el propio dispositivo: las prendas en `localStorage` y las fotos en
IndexedDB. No hay cuentas ni servidor.

## Usarla
Abrí el link publicado en el celular y agregala a la pantalla de inicio.
Para probarla en la computadora, serví la carpeta con cualquier servidor estático:

```bash
python -m http.server 8787
```

y abrí http://localhost:8787. (Abrir `index.html` directo con doble clic no
alcanza porque el service worker y la cámara necesitan un servidor.)

## Funciones
- **Hoy**: tres looks sugeridos según temporada, pronóstico, lo usado en la
  semana y lo que está en lavado. Toggle de "reunión importante".
- **Placard**: inventario con foto, categoría, color, temporadas y formalidad.
  Estados: disponible, en lavado, guardada de temporada. Sesión de inventario
  para sacar muchas fotos seguidas y clasificar después.
- **Link de compra**: al pegar el link del producto, la app intenta traer la foto
  de la tienda (usa api.microlink.io para leer la página e images.weserv.nl para
  descargar la imagen con permiso de origen cruzado). Si falla, se puede sacar
  la foto o elegirla de la galería.
- **Looks**: combinaciones guardadas, armador manual con chequeo de colores.
- **Viajes**: cápsula según días, clima y reuniones, plan por día y checklist
  de valija con tildes. Las cápsulas se guardan y se pueden duplicar.
- **Pronóstico**: opcional, con la ciudad configurada en Ajustes (Open-Meteo,
  sin clave). Sin ciudad, usa la temperatura típica de la temporada.
- **Copia de seguridad**: exportar e importar todo (incluidas fotos) como JSON.

## Servicios externos
Solo se consultan cuando hace falta y nunca reciben datos personales:
Open-Meteo (pronóstico y búsqueda de ciudad), Microlink (foto de un link de
compra), weserv.nl (descarga de esa foto), Google Fonts.
