# Manual de uso: CRM Ventas

Guía para usar la página día a día. Se explica en el orden en que normalmente se trabaja.

## 1. Conceptos básicos

**Las tres tasas.** Arriba de la página siempre ves las tasas actuales:
- **Oficial:** la tasa del BCV. Se usa para pasar a dólares y para valorar el costo de las compras en dólares.
- **Binance:** la tasa del dólar paralelo.
- **Tasa de venta:** el promedio entre la oficial y la Binance. Con ella se calculan los precios de venta.

Junto a las tasas aparece la **fecha y hora de la última publicación** de datos (ver sección 11).

**Presentaciones.** Cada producto se vende por **unidad**, **caja** (por ejemplo 20 unidades) o **brazo** (por ejemplo 10 cajas).

**Precio de venta de un producto.**
- Si el producto tiene **precio manual por unidad**, se usa ese precio.
- Si no lo tiene, la página calcula un sugerido con el costo, el porcentaje de ganancia y la tasa.
- El precio de la caja y del brazo sale de multiplicar el precio de la unidad.

**Costo.** Cada compra guarda su propio costo y su tasa. El costo del inventario se maneja como **promedio ponderado**: si compras a precios distintos, el costo por unidad es el promedio de lo que tienes en existencia.

**Ventas ya registradas.** Cada venta guarda el costo, las tasas y el precio del momento. Si después cambian los costos o las tasas, el historial no se modifica.

## 2. Menú y pantalla de inicio

Las pestañas están fijas en la parte de arriba y se ven aunque bajes la pantalla: **Resumen, Vender, Inventario, Compras, Deudores, Tesorería, Tasas y Admin** (según tu usuario, ver la sección 17). El historial de ventas está al final de **Vender**. En la esquina superior derecha hay un botón para cambiar entre tema claro y oscuro (ver la sección 18).

### Pestaña Resumen

- **Vendido hoy** y **ganancia de hoy**.
- **Inventario a costo:** lo que te costó la mercancía que tienes. Va en bolívares y dólares (a la tasa oficial).
- **Inventario a precio de venta:** lo que obtendrías si vendes todo al precio actual.
- **Ganancia del inventario:** la diferencia entre las dos anteriores.
- **Ganancia del mes:** en bolívares y en dólares a la tasa oficial.
- **Por cobrar:** lo que te deben los clientes.
- **Revisar precios:** productos cuyo precio manual está por debajo o muy por encima del sugerido.
- **Inventario: costo y ganancia por producto:** tabla con el stock, el costo, el precio y la ganancia de cada producto, con montos en bolívares y dólares.
- **Hay que reponer:** productos con 25 unidades o menos, con un **sugerido de compra** según su rotación (ver sección 9).
- **Cobros por tipo de pago:** gráfico de barras verticales con el dinero cobrado en **efectivo bolívares**, **transferencia** y **divisas** (efectivo en dólares y dólares en línea), para ver cuál es el método de pago más usado. Tiene los mismos filtros de periodo (por defecto, General) y debajo dice cuál es el método más usado.
- **Más vendidos:** gráfico de barras con las unidades vendidas por producto. Tiene filtros: **Hoy**, **Semana** (los últimos 7 días, contando hoy), **Este mes**, **General** (todos los registros) y una lista **Mes anterior** para elegir un mes pasado.

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

### Modificar un producto

Los productos nuevos ya no se crean desde Inventario: se crean al registrar una compra con la opción **+ Crear producto** (sección 6). Para cambiar un producto que ya existe, toca **Editar** en su fila: se abre la ventana **Modificar producto** con nombre, tamaño, unidades por caja, cajas por brazo, costo por caja, factor de ganancia (1,4 es 40 %), precio manual y aviso de reposición. **Guardar** aplica el cambio y **Cancelar** lo descarta. Con **Desactivar** el producto deja de aparecer en las listas sin borrar su historial.

### Qué muestra la tabla

- **Búsqueda:** escribe el nombre del producto y la lista se filtra mientras escribes.
- **Columnas:** producto, stock (en unidades y en cajas y unidades), precio por unidad con su semáforo, precio de la caja, del brazo y valor a costo. Caja, brazo y valor muestran también el monto en dólares a la tasa oficial.
- **Productos inactivos:** salen con las letras en gris y la etiqueta "inactivo".
- **Botones:** **Editar** y **Desactivar** siempre van uno al lado del otro.

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
   Si la venta es de contado, elige también el **tipo de pago** (pago móvil / transferencia, efectivo bolívares, efectivo dólares o dólares en línea). Es obligatorio. Si el tipo es en dólares, se guarda el equivalente en dólares a la tasa de venta del momento. Si pagaron con dos tipos distintos, registra la venta como fiado y luego un abono por cada tipo.
5. Si no pagó todo, marca la opción de **fiado**. Para fiar necesitas indicar el cliente.
6. Toca **Registrar venta**.

Al registrar la venta, el inventario baja y la ganancia se calcula con el costo promedio del momento.

La página no te deja agregar más cantidad de la que hay en stock.

**Código de venta.** Cada venta registrada recibe un código automático y único con el formato **V000000**: una V mayúscula y seis dígitos que van subiendo de uno en uno (V000000, V000001, V000002…). No se puede escribir ni cambiar a mano, y nunca se repite. Las ventas anteriores a este cambio recibieron su código por orden de fecha. Antes de asignarlo, la página descarga lo publicado para continuar la numeración. Si dos dispositivos registraran ventas a la vez sin sincronizar y coincidieran dos códigos, la venta más reciente recibe el siguiente número libre.

### Historial de ventas

Está al final de la pestaña **Vender**.

- **Filtros:** escribe un **nombre de cliente** o un **número de factura** (completo, como V000012, o solo los dígitos, como 000012) y filtra por **estado**: contado, debe (fiado pendiente), pagado (fiado) o anulada.
- **Columnas:** N° factura, fecha, cliente, total, ganancia, estado y acciones.
- **🧾 Recibo:** abre una ventana tipo recibo con el número de factura, el cliente, la fecha y la hora, cada producto con su cantidad, su precio en bolívares y en dólares, el total y, si hubo descuento, el porcentaje aplicado. **Volver al historial** cierra la ventana.
- **Anular:** el botón está a la derecha del recibo, separado para no tocarlo por error. Pide confirmación en una ventana ("Sí, anular" o "Cancelar"). Al anular, los productos vuelven al inventario y la venta deja de contar en los totales. El código de la venta anulada no se vuelve a usar.
- **Exportar a Excel** incluye el número de factura.

### Cotización en PDF

El botón **Descargar cotización (PDF)** genera un documento con los productos que tienes en la venta: producto, cantidad, precio y subtotal en bolívares y en dólares, y el total. Sirve para mostrarle el precio al cliente.

**La cotización no registra la venta y no rebaja el inventario.** El inventario solo baja cuando tocas **Registrar venta**.

## 6. Compras

Para registrar mercancía que entra, toca **Registrar nueva compra** (el botón ancho y centrado de arriba). Se abre una ventana con estos datos:
- **N° de factura** de la compra (opcional). Si registras varios productos con el mismo número, quedan agrupados en una sola factura.
- **Producto:** lista sin nombres repetidos. La última opción es **+ Crear producto**, que muestra los datos del producto nuevo (nombre, tamaño, unidades por caja, cajas por brazo, % de ganancia y precio manual opcional) para crearlo al guardar la compra. Si ya existe un producto con ese nombre, la página avisa y pide elegirlo de la lista.
- **Comprado por** caja o brazo, **cantidad**, **moneda** (dólares o bolívares), **costo por caja**, **tasa** (si la dejas vacía, usa la oficial) y **proveedor**.
- **¿Con qué pagaste? (opcional):** cuánto pagaste de cuenta bancaria, de efectivo en bolívares, de efectivo en dólares y con dólares en línea. Lo que no indiques queda como "Sin tipo" y lo puedes asignar después en Tesorería. Si lo pagado supera el total de la compra, no te deja guardar.

En el teléfono los datos aparecen uno encima del otro; en el computador se ordenan en varias columnas. **Guardar compra** suma el stock, guarda el costo real, actualiza el costo del producto y **descuenta la compra en Tesorería** (ver la sección 8). **Cancelar** cierra la ventana. Las compras anteriores y las ventas ya hechas no cambian.

**Compras recientes** agrupa las compras por **número de factura** y muestra, por cada una, el N° de factura, la fecha, el total de cajas y el **total** de la factura. Las compras sin número de factura salen cada una por separado. El botón **Ver registro** abre una ventana con todos los datos: factura, fecha, proveedor y, por cada producto, cajas, unidades, moneda, costo por caja, tasa, total y con qué se pagó. Puedes filtrar por **número de factura o producto** y por **día** (calendario); **Limpiar** quita los filtros. El botón **Exportar a Excel** descarga el detalle de todas las compras, una fila por producto, con el número de factura.

Cuando suba o baje el costo de un producto, registra siempre la compra nueva y revisa después los semáforos de precios.

## 7. Deudores (antes Fiados)

La pestaña muestra:
- **Cuentas por cobrar:** cada cliente con el **total de su deuda** en grande y centrado, y las fechas de sus ventas pendientes. El botón **Ver detalle** abre una ventana con cada venta pendiente (código, fecha, productos con cantidad, precio en bolívares y en dólares, lo abonado y lo que debe) y el total que debe. **Volver** cierra la ventana.
- **Registrar abono:** toca el botón y se abre una ventana donde eliges el **tipo de pago** (pago móvil / transferencia, efectivo bolívares, efectivo dólares o dólares en línea) y escribes el **monto que te pagaron**. Si el tipo es en dólares, el monto se escribe en dólares y la página lo convierte a bolívares con la **tasa de venta** del momento para restarlo de la deuda. Al tocar **Guardar registro** aparece otra ventana con el resumen (cliente, tipo de pago, monto, equivalente, deuda actual y deuda después). Si todo está bien, toca **Aceptar** y el pago queda guardado. Si tocas **Cancelar** en el resumen, vuelves a la ventana anterior con los datos que escribiste. El abono se aplica primero a las deudas más antiguas.
- **✏️ (lápiz):** junto a cada cliente, sirve para corregir su nombre. El cambio se aplica también a sus ventas anteriores.
- **Pagos recibidos:** tabla con la fecha de cada abono o pago, el cliente, el monto, el tipo de pago, de qué deuda es y si fue un **Abono** o **Pagó completo**.
- **Marcar abonos sin tipo como efectivo bolívares:** botón que aparece en **Pagos recibidos** solo si hay abonos registrados antes de existir el tipo de pago. Pide confirmación y les asigna "efectivo bolívares". Después de usarlo, desaparece.
- **✏️ en Pagos recibidos:** junto al tipo de pago de cada abono hay un lápiz para corregirlo si te equivocaste. Abre una ventana con los datos del pago y una lista con el nuevo tipo; **Guardar** aplica el cambio y **Cancelar** lo descarta. El monto en bolívares que se abonó a la deuda no cambia. Si pasas de bolívares a dólares, se guarda el equivalente en dólares con la tasa de venta de ese momento. El cambio se refleja en Tesorería.
- **Clientes al corriente:** los que no deben nada.

El botón **Exportar a Excel** crea un archivo con dos hojas: las deudas y los pagos recibidos.

## 8. Tesorería

Sirve para controlar el dinero que cobras, el que usas y el que te queda. Solo la ve el administrador.

**Filtros de periodo:** arriba puedes ver todo de **Hoy**, **Semana** (los últimos 7 días, contando hoy), **Este mes**, un **Mes anterior** (lista desplegable) o **General**. Al abrir, la pestaña muestra el general. Las alertas se calculan con el periodo que estés viendo, y el Excel exportado también.

**Los seis cuadros de arriba:**
- **Total cobrado:** ventas de contado más abonos y pagos de fiados.
- **Ganancia cobrada:** la parte de ganancia de lo cobrado. En los fiados se cuenta en proporción a lo abonado.
- **Dinero para reposición de mercancía:** total cobrado menos ganancia cobrada, menos las compras registradas. Es el dinero que se descuenta cuando registras una compra. Si una compra lo supera, sale una alerta roja que dice que estás usando parte de tus ganancias para reponer mercancía y el cuadro muestra el **excedente en negativo**.
- **Dinero usado:** las compras más el dinero usado que registres a mano.
- **Disponible para usar:** total cobrado menos el dinero usado, más las reposiciones de dinero.
- **Ganancia disponible:** la ganancia cobrada menos lo que usaste a mano y menos el excedente de las compras. Una compra no la toca mientras no supere el dinero para reposición. Su monto sale en **verde esmeralda** cuando es mayor que 0.

*Ejemplo:* cobraste 20.000 Bs y 5.000 son ganancia, así que 15.000 son para reponer mercancía. Registras una compra de 12.000: el cuadro de reposición queda en 3.000 y la ganancia disponible sigue en 5.000. Si la compra fuera de 17.000, la reposición mostraría −2.000 con la alerta, y la ganancia disponible bajaría a 3.000.

**Alertas:** roja si lo usado de tus ganancias supera la ganancia cobrada (ganancia disponible negativa); amarilla si queda el 20 % o menos de la ganancia cobrada; sin color si no se cumple ninguna.

**Dinero por tipo:** separa lo que tienes según cómo te pagaron o repusiste: **efectivo en dólares**, **efectivo en bolívares**, **dinero en cuenta bancaria** (pago móvil y transferencia) y **dólares en línea**. Cada cuadro muestra lo cobrado, lo repuesto y lo usado. Las ventas de contado anteriores a existir el tipo de pago aparecen aparte como "Sin especificar". Si el monto bajó más de **60 %** respecto a lo cobrado y repuesto en ese tipo, sale en amarillo; si bajó más de **90 %**, en rojo. Debajo hay un **gráfico en 3D** (los dólares se pasan a bolívares con la tasa de venta actual).

**Contado vs fiado:** gráfico de torta con el dinero cobrado de cada uno y su ganancia.

**Registrar dinero usado o reposición:** elige el **movimiento**:
- **Dinero usado:** escribe el concepto, elige **de dónde salió el dinero** (los cuatro tipos), el monto y, si quieres, la fecha. El monto se escribe en dólares si el tipo es en dólares.
- **Reposición de dinero:** úsala cuando repongas, con dinero de otra fuente, lo que tomaste de tus ganancias. Elige **a qué tipo de pago lo repones** y el monto. Suma al tipo elegido y restituye primero el excedente de las compras y luego el dinero usado a mano. Lo que sobre pasa al dinero para reposición de mercancía.

Para los totales, los dólares se pasan a bolívares con la tasa de venta del momento.

**Gráfico del dinero usado** (incluye las compras): cambia según el filtro. En **General** muestra un mes por barra desde el primer registro del CRM; en **Este mes** y **Mes anterior**, una barra por semana calendario de lunes a domingo (la primera semana empieza el día 1 y la última termina el último día del mes); en **Semana**, una barra por día; y en **Hoy**, una barra por tipo de pago.

**Dinero usado (lista):** muestra los gastos que registraste, con **Eliminar**, y las compras, con la etiqueta "Compra". En las compras, el botón **Cambiar pago** abre una ventana para indicar cuánto pagaste de cuenta bancaria, de efectivo y de dólares. Lo que falte hasta el total queda como "Sin tipo". Los gastos y compras sin tipo se descontaron primero del efectivo y luego de la cuenta o de los dólares en línea. **Reposiciones de dinero (lista):** las que registraste, con **Eliminar**. Abajo está **Cobros recibidos** (fecha, cliente, tipo, medio de pago, monto y ganancia) y el botón **Exportar a Excel**, que descarga el resumen, el dinero por tipo, los cobros, el dinero usado y las reposiciones.

Las ventas anuladas no cuentan como dinero cobrado. Todo se sincroniza igual que las ventas.

## 9. Reposición: cómo se calcula el sugerido de compra

En **Hay que reponer** aparecen los productos con 25 unidades o menos. El sugerido depende de cuánto se vendió en los últimos 30 días:

| Rotación | Qué significa | Sugerido |
|---|---|---|
| Alta | Se vendió más cajas de las que compraste la última vez | La cantidad de la última compra más 25 % (mínimo 1 caja más) |
| Normal | Se vendió algo, pero no más que la última compra | La misma cantidad de la última compra |
| Sin movimiento | No se vendió nada | 1 a 2 cajas |

Si el producto todavía no tiene compras registradas, la página usa como base lo que se vendió en 30 días. Para que el sugerido sea más útil, registra tus compras en la pestaña **Compras**.

## 10. Historial

El historial de ventas ya no tiene pestaña propia: está al final de **Vender** (ver la sección 5).

## 11. Usar la página en varios dispositivos

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

## 12. Instalar la página como app

1. **iPhone:** abre la dirección en **Safari**, toca **Compartir** y luego **Agregar a pantalla de inicio**.
2. **Android:** abre la dirección en **Chrome**, toca los tres puntos y luego **Instalar aplicación** (o **Agregar a pantalla principal**).

La app se llama **CRM Ventas** y usa el logo de Bigott como ícono. Si ya la tenías instalada con otro nombre, bórrala de la pantalla de inicio y vuelve a agregarla.

En iPhone, la app instalada guarda sus datos aparte de Safari. Si usaste la página en Safari antes de instalarla, publica los cambios desde ahí primero para que la app los descargue al abrirse.

## 13. Exportar a Excel y PDF

- **Excel:** Inventario, Compras, Historial, Fiados y Tesorería.
- **PDF:** cotización en la pestaña Vender.

Las exportaciones necesitan internet, porque descargan una librería en el momento. En iPhone con la app instalada, la descarga a veces no funciona; si pasa, abre la página en Safari y exporta desde ahí.

## 14. Cómo actualizar la página

Cuando se hagan ajustes nuevos al código:
1. Entra al repositorio en GitHub.
2. Toca **Add file → Upload files**.
3. Sube el archivo nuevo con el mismo nombre y toca **Commit changes**.
4. Espera un minuto y recarga. En la app instalada, ciérrala del todo y ábrela de nuevo.

Tus datos no se pierden al cambiar el archivo.

## 15. Problemas frecuentes

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

## 16. Recomendaciones

- Publica los cambios al terminar de registrar, sobre todo antes de que otra persona use la página.
- Registra siempre las compras en **Compras** y no por ajustes, para que el costo promedio sea correcto.
- Revisa los semáforos de precios cuando cambie la tasa o el costo de un producto.
- Cuida el token de GitHub como una clave: si lo compartes por error, bórralo en GitHub y crea uno nuevo.
- Si necesitas privacidad en las ventas y los fiados, considera un repositorio privado o una base de datos con inicio de sesión.

## 17. Inicio de sesión y usuarios

Al abrir la página aparece primero un cuadro para escribir **usuario y clave**. La sesión se queda guardada en ese dispositivo hasta que toques **Cerrar sesión** (en la barra de las tasas).

Hay dos usuarios:
- **administrador:** ve todas las pestañas.
- **ventas:** solo ve **Vender** (con su historial), **Deudores**, **Tasas** y **Admin** (para publicar cambios).

**Gestionar usuarios (solo el administrador).** Al final de **Admin** aparece la tarjeta **Usuarios**, con el usuario, el rol, la clave y el estado. Cada fila tiene dos botones:
- **Cambiar clave:** abre una ventana para escribir la clave nueva dos veces (mínimo 4 caracteres).
- **Desactivar / Activar:** un usuario desactivado no puede entrar. Nadie puede desactivar su propio usuario.

En el inicio de sesión y en la ventana de cambio de clave hay un ícono de **ojo** para ver u ocultar lo que escribes. Las claves se guardan cifradas, por eso la tarjeta de usuarios no las muestra; si alguien la olvida, el administrador usa **Cambiar clave** para poner una nueva. Los cambios de usuarios y claves se sincronizan al tocar **Publicar cambios**.

**Importante:** este acceso sirve para evitar usos casuales, pero no es seguridad fuerte. La página y los archivos publicados son públicos si el repositorio es público, así que alguien con conocimientos técnicos podría saltarse el acceso. Para proteger de verdad las ventas, usa un repositorio privado o un servicio con inicio de sesión real.

## 18. Tema claro y oscuro

La página se abre con el tema que tenga tu dispositivo (claro u oscuro). En la esquina superior derecha, siempre visible, hay un botón para cambiarlo: con tema claro muestra una media luna (cambia a oscuro) y con tema oscuro muestra un sol (cambia a claro). En el computador, al pasar el cursor aparece una nota con el tema al que va a cambiar. El cambio dura mientras tengas la página abierta; al volver a abrirla se usa otra vez el tema del dispositivo.
