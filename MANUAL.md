# Manual de uso: CRM Ventas

Guía para usar la página día a día. Se explica en el orden en que normalmente se trabaja.

## 1. Conceptos básicos

**Las tres tasas.** Arriba de la página siempre ves las tasas actuales:
- **Oficial:** la tasa del BCV. Se usa para pasar a dólares y para valorar el costo de las compras en dólares.
- **Binance:** la tasa del dólar paralelo.
- **Tasa de venta:** el promedio entre la oficial y la Binance. Con ella se calculan los precios de venta.

Junto a las tasas aparece la **fecha y hora de la última publicación** de datos (ver sección 10).

**Presentaciones.** Cada producto se vende por **unidad**, **caja** (por ejemplo 20 unidades) o **brazo** (por ejemplo 10 cajas).

**Precio de venta de un producto.**
- Si el producto tiene **precio manual por unidad**, se usa ese precio.
- Si no lo tiene, la página calcula un sugerido con el costo, el porcentaje de ganancia y la tasa.
- El precio de la caja y del brazo sale de multiplicar el precio de la unidad.

**Costo.** Cada compra guarda su propio costo y su tasa. El costo del inventario se maneja como **promedio ponderado**: si compras a precios distintos, el costo por unidad es el promedio de lo que tienes en existencia.

**Ventas ya registradas.** Cada venta guarda el costo, las tasas y el precio del momento. Si después cambian los costos o las tasas, el historial no se modifica.

## 2. Menú y pantalla de inicio

Las pestañas están fijas en la parte de arriba y se ven aunque bajes la pantalla: **Resumen, Vender, Inventario, Compras, Fiados, Historial, Tasas y Admin**.

### Pestaña Resumen

- **Vendido hoy** y **ganancia de hoy**.
- **Inventario a costo:** lo que te costó la mercancía que tienes. Va en bolívares y dólares (a la tasa oficial).
- **Inventario a precio de venta:** lo que obtendrías si vendes todo al precio actual.
- **Ganancia del inventario:** la diferencia entre las dos anteriores.
- **Ganancia del mes:** en bolívares y en dólares a la tasa oficial.
- **Por cobrar:** lo que te deben los clientes.
- **Revisar precios:** productos cuyo precio manual está por debajo o muy por encima del sugerido.
- **Inventario: costo y ganancia por producto:** tabla con el stock, el costo, el precio y la ganancia de cada producto, con montos en bolívares y dólares.
- **Hay que reponer:** productos con 25 unidades o menos, con un **sugerido de compra** según su rotación (ver sección 8).
- **Más vendidos:** gráfico de barras con las unidades vendidas por producto. Tiene tres botones: **Hoy**, **Este mes** y **General** (todos los registros).

## 3. Tasas

1. Entra a la pestaña **Tasas**.
2. Toca **Actualizar tasas automáticamente** para traer la tasa oficial y el dólar paralelo. Se guardan con la fecha de hoy.
3. Si prefieres, escribe las dos tasas a mano y toca **Guardar tasa de hoy**.

Detalles importantes:
- La actualización automática **solo funciona en la versión de GitHub** y necesita internet. Si falla, te muestra el motivo y puedes escribir las tasas a mano.
- El dato de "Binance" viene del dólar paralelo de un servicio externo (DolarApi, basado en Yadio). Es una aproximación y puede diferir un poco del precio que ves en la app de Binance. Si necesitas el valor exacto, escríbelo a mano.
- Si la tasa oficial cambia más de 25 % de golpe, la página te pide confirmación antes de guardar, por si hubo un error al escribirla.
- Se conserva un historial de tasas.

## 4. Inventario

### Crear o editar un producto

Los datos de cada producto son:
- **Nombre** y **tamaño** (grande o pequeño).
- **Unidades por caja** y **cajas por brazo**.
- **Costo por caja** en dólares.
- **Factor de ganancia** (por ejemplo 1,4 significa 40 % de ganancia sobre el costo).
- **Precio manual por unidad** en bolívares (opcional).

Con **Editar** cambias cualquier dato. Con **Desactivar** el producto deja de aparecer sin borrar su historial.

### Qué muestra la tabla

Por producto: stock en unidades y en cajas y unidades (por ejemplo "1 caja y 16 unidades"), costo promedio por unidad, valor del stock a costo, precio por unidad, caja y brazo, y los semáforos.

### Semáforo de precios

Compara tu precio manual con el sugerido:
- 🔴 **Subir:** tu precio está por debajo del sugerido.
- 🟡 **OK:** tu precio está en un rango normal.
- 🟢 **Puede bajar:** tu precio está más de 10 % por encima del sugerido.

### Semáforo de existencias

- 🔴 **Agotado:** no queda nada.
- 🔴 **Reponer:** 25 unidades o menos.
- 🟡 **Por acabarse:** de 26 a 59 unidades.
- 🟢 **OK:** más de 59 unidades.

### Ajustes de inventario

Sirven para corregir el stock sin pasar por una compra o una venta. Hay estos motivos: **Conteo inicial**, **Merma**, **Robo**, **Error de conteo** y **Consumo propio**.

- Usa **Conteo inicial** una sola vez, al empezar, para cargar lo que ya tienes. Se valora con el costo por caja del producto y la tasa oficial del momento.
- Para quitar mercancía escribe una cantidad negativa o usa el motivo que corresponda.

Cuando el costo real es distinto al costo del producto, registra mejor una **compra** (sección 6).

### Exportar

El botón **Exportar a Excel** descarga el inventario con las columnas de tu Excel original (venta por unidad, por caja, cajetín, brazo y ganancias) con sus fórmulas, la tabla de tasas al final y el stock, el costo promedio y la ganancia potencial a la derecha.

## 5. Vender

1. Elige el **producto**, la **presentación** (unidad, caja o brazo) y la **cantidad**.
2. Si es una venta con descuento, escribe el **precio especial por unidad**. La página te dice el porcentaje de descuento. Ejemplo: caja de 20 unidades con precio normal de 80 Bs por unidad (1.600 Bs la caja) y precio especial de 67 Bs por unidad, queda en 1.340 Bs la caja, un descuento de 16,25 %.
3. Toca **Agregar**. Puedes agregar varios productos, cada uno con su propio precio especial.
4. Elige el **cliente**: sin cliente (contado), uno que ya existe o uno nuevo.
5. Si no pagó todo, marca la opción de **fiado**. Para fiar necesitas indicar el cliente.
6. Toca **Registrar venta**.

Al registrar la venta, el inventario baja y la ganancia se calcula con el costo promedio del momento.

La página no te deja agregar más cantidad de la que hay en stock.

### Cotización en PDF

El botón **Descargar cotización (PDF)** genera un documento con los productos que tienes en la venta: producto, cantidad, precio y subtotal en bolívares y en dólares, y el total. Sirve para mostrarle el precio al cliente.

**La cotización no registra la venta y no rebaja el inventario.** El inventario solo baja cuando tocas **Registrar venta**.

## 6. Compras

Para registrar mercancía que entra:
1. Elige el producto y si compras por caja o por brazo, y la cantidad.
2. Indica la moneda (dólares o bolívares) y el costo por caja.
3. Indica la tasa de la compra. Si la dejas vacía, usa la oficial.
4. Escribe el proveedor (por ejemplo Bigott) y toca registrar.

La compra suma el stock, guarda su costo real y actualiza el **costo del producto**, que es el que usa la página para sugerir precios. Las compras anteriores y las ventas ya hechas no cambian.

Cuando suba o baje el costo de un producto, registra siempre la compra nueva y revisa después los semáforos de precios.

La lista de **Compras recientes** tiene el botón **Exportar a Excel**.

## 7. Fiados

La pestaña muestra:
- **Cuentas por cobrar:** cada cliente con lo que debe, y el detalle de las ventas pendientes.
- **Abonos:** escribe el monto que paga el cliente y regístralo. El abono se aplica primero a las deudas más antiguas.
- **Editar nombre:** corrige el nombre de un cliente. El cambio se aplica también a sus ventas anteriores.
- **Pagos recibidos:** tabla con la fecha de cada abono o pago, el cliente, el monto, de qué deuda es y si fue un **Abono** o **Pagó completo**.
- **Clientes al corriente:** los que no deben nada.

El botón **Exportar a Excel** crea un archivo con dos hojas: las deudas y los pagos recibidos.

## 8. Reposición: cómo se calcula el sugerido de compra

En **Hay que reponer** aparecen los productos con 25 unidades o menos. El sugerido depende de cuánto se vendió en los últimos 30 días:

| Rotación | Qué significa | Sugerido |
|---|---|---|
| Alta | Se vendió más cajas de las que compraste la última vez | La cantidad de la última compra más 25 % (mínimo 1 caja más) |
| Normal | Se vendió algo, pero no más que la última compra | La misma cantidad de la última compra |
| Sin movimiento | No se vendió nada | 1 a 2 cajas |

Si el producto todavía no tiene compras registradas, la página usa como base lo que se vendió en 30 días. Para que el sugerido sea más útil, registra tus compras en la pestaña **Compras**.

## 9. Historial

Lista todas las ventas con fecha, cliente, detalle (con el descuento si lo hubo), total, estado (contado, pagado, debe o anulada).

- **Anular una venta** devuelve los productos al inventario y la saca de los totales. Úsalo solo cuando te equivocaste al registrarla.
- **Exportar a Excel** descarga todas las ventas con costo, ganancia y las tasas que se usaron en cada una.

## 10. Usar la página en varios dispositivos

Los datos se guardan en el navegador de cada dispositivo, no en la nube. Para compartirlos se usa la **publicación en GitHub**:

1. Entra a la pestaña **Admin**.
2. Escribe el token de GitHub (solo la primera vez en cada dispositivo) y toca **Guardar y probar conexión**.
3. Después de registrar ventas, compras o cambios, toca **Publicar cambios**.
4. En el otro dispositivo, espera cerca de un minuto, abre la página (o recárgala) y verás lo publicado.

Cómo se combinan los datos:
- Al abrir la página se descargan los datos publicados y se unen con los del dispositivo.
- Al publicar, primero se leen los datos de GitHub y se unen con los locales, para no borrar lo que registró el otro dispositivo.
- Si el mismo registro se editó en dos dispositivos, se queda la versión editada más recientemente.

Lo que debes tener presente:
- **Si no publicas, el otro dispositivo no ve el cambio.** Cada persona que registre ventas debe tocar **Publicar cambios** al terminar.
- **No es en tiempo real.** Los datos se actualizan al abrir la página.
- Lo más seguro es que **un solo dispositivo registre a la vez** y que publique antes de que el otro empiece.
- El token se guarda solo en el navegador donde lo escribiste; en cada dispositivo hay que ponerlo una vez.

## 11. Instalar la página como app

1. **iPhone:** abre la dirección en **Safari**, toca **Compartir** y luego **Agregar a pantalla de inicio**.
2. **Android:** abre la dirección en **Chrome**, toca los tres puntos y luego **Instalar aplicación** (o **Agregar a pantalla principal**).

La app se llama **CRM Ventas** y usa el logo de Bigott como ícono. Si ya la tenías instalada con otro nombre, bórrala de la pantalla de inicio y vuelve a agregarla.

En iPhone, la app instalada guarda sus datos aparte de Safari. Si usaste la página en Safari antes de instalarla, publica los cambios desde ahí primero para que la app los descargue al abrirse.

## 12. Exportar a Excel y PDF

- **Excel:** Inventario, Compras, Historial y Fiados.
- **PDF:** cotización en la pestaña Vender.

Las exportaciones necesitan internet, porque descargan una librería en el momento. En iPhone con la app instalada, la descarga a veces no funciona; si pasa, abre la página en Safari y exporta desde ahí.

## 13. Cómo actualizar la página

Cuando se hagan ajustes nuevos al código:
1. Entra al repositorio en GitHub.
2. Toca **Add file → Upload files**.
3. Sube el archivo nuevo con el mismo nombre y toca **Commit changes**.
4. Espera un minuto y recarga. En la app instalada, ciérrala del todo y ábrela de nuevo.

Tus datos no se pierden al cambiar el archivo.

## 14. Problemas frecuentes

**No veo en un dispositivo lo que registré en otro.**
Revisa que el primer dispositivo haya tocado **Publicar cambios**. Después espera un minuto y recarga el segundo. Abre en el teléfono `datos/ventas.json` del sitio para confirmar si la venta ya está publicada.

**El costo promedio y el valor salen en 0.**
Pasa cuando el stock se cargó sin costo. Los conteos iniciales se valoran con el costo del producto; revisa que ese costo no sea 0. Si el stock entra por mercancía nueva, registra una compra.

**La actualización automática de tasas da error.**
Puede ser falta de internet o que el servicio externo no esté disponible. Escribe las tasas a mano y toca **Guardar tasa de hoy**.

**El Excel o el PDF no se descarga.**
Revisa tu internet. En iPhone con la app instalada, prueba desde Safari.

**Aparece una X roja junto a los archivos de `datos` en GitHub.**
Es el estado de la última comprobación de GitHub sobre esa confirmación, no un daño en el archivo. Si los datos se ven bien en la página, puedes ignorarla.

**La página no muestra los cambios nuevos.**
Recarga sin usar la memoria del navegador (Ctrl + F5 en computadora) o cierra del todo la app instalada y vuelve a abrirla.

**Borré los datos del navegador.**
Se pierde lo que no estaba publicado. Lo ya publicado se recupera al abrir la página. Por eso conviene publicar al final de cada jornada.

## 15. Recomendaciones

- Publica los cambios al terminar de registrar, sobre todo antes de que otra persona use la página.
- Registra siempre las compras en **Compras** y no por ajustes, para que el costo promedio sea correcto.
- Revisa los semáforos de precios cuando cambie la tasa o el costo de un producto.
- Cuida el token de GitHub como una clave: si lo compartes por error, bórralo en GitHub y crea uno nuevo.
- Si necesitas privacidad en las ventas y los fiados, considera un repositorio privado o una base de datos con inicio de sesión.
