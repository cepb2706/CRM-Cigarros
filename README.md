# CRM Ventas

Página web para llevar el inventario, las ventas, las compras y los fiados de un negocio de cigarros. Funciona en el navegador del computador y del teléfono, y se puede instalar como app.

Dirección de la página: https://cepb2706.github.io/CRM-Cigarros/

## Qué hace

- **Resumen:** ventas y ganancia del día y del mes, inventario a costo y a precio de venta, ganancia estimada del inventario, cuentas por cobrar, productos por reponer con sugerido de compra y gráfico de los más vendidos.
- **Vender:** registra ventas por unidad, caja o brazo, con precio especial opcional (muestra el porcentaje de descuento), ventas de contado o fiadas y cotización en PDF.
- **Inventario:** productos, costos, precios, ajustes de stock y semáforo de alertas (precios y existencias).
- **Compras:** registra compras en dólares o bolívares y actualiza el costo y el stock.
- **Fiados:** deudas por cliente, abonos con ventana de registro y confirmación, tipo de pago (pago móvil / transferencia, efectivo bolívares, efectivo dólares o dólares en línea), fecha de cada pago y edición del nombre del cliente.
- **Tesorería:** dinero cobrado (contado, abonos y pagos de fiados), dinero usado (en dólares o bolívares) que registras a mano, saldos separados por tipo de pago, lo disponible y alertas de color si lo usado supera la ganancia cobrada.
- **Historial:** todas las ventas, con opción de anularlas.
- **Tasas:** tasa oficial (BCV), tasa Binance y tasa de venta, con actualización automática.
- **Admin:** publica los datos en GitHub para verlos en otros dispositivos.
- **Exportar:** Excel en Inventario, Compras, Historial, Fiados y Tesorería; PDF de cotización en Vender.

## Archivos del repositorio

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La página completa (código y diseño) |
| `manifest.json` | Datos para instalarla como app (nombre "CRM Ventas") |
| `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` | Ícono de la app (logo de Bigott) |
| `datos/ventas.json` | Ventas, clientes y dinero usado publicados |
| `datos/inventario.json` | Productos, movimientos de inventario y compras |
| `datos/config.json` | Tasas de cambio y su historial |
| `MANUAL.md` | Manual de uso |

La carpeta `datos` la crea y actualiza la propia página cuando tocas **Publicar cambios**. No la edites a mano.

## Cómo funciona el guardado

Los datos se guardan en el navegador de cada dispositivo. Para compartirlos, la página los publica en la carpeta `datos` del repositorio y los demás dispositivos los descargan al abrirla. No es en tiempo real: hay que publicar después de registrar y esperar cerca de un minuto. Los detalles están en `MANUAL.md`.

## Cómo actualizar la página

1. Entra al repositorio en GitHub.
2. Toca **Add file → Upload files**.
3. Sube el `index.html` nuevo con el mismo nombre y toca **Commit changes**.
4. Espera un minuto y recarga la página. Tus datos no se pierden, porque se guardan aparte del archivo.

## Seguridad

- Si el repositorio es público, cualquiera que encuentre los archivos de `datos` puede ver las ventas, los clientes y las deudas publicadas.
- El token de GitHub que usas en la pestaña **Admin** da permiso de escritura en el repositorio. No lo compartas ni lo pegues en chats.

## Tecnología

Una sola página HTML con JavaScript, sin servidor propio. Se publica con GitHub Pages. Las exportaciones usan las librerías SheetJS (Excel) y jsPDF (PDF), que se descargan al momento de exportar.
