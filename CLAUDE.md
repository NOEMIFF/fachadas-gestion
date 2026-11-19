# Gestión de fachadas ventiladas

App de gestión de una empresa de fachadas ventiladas (~25 personas). Es obra real: la geometría debe ser exacta.

## Código
- Todo vive en `prototipo-gestion.html` (un único archivo con CSS, JS, three.js y supabase-js). Edítalo directamente.
- Versión visible: constante `APP_VER` (formato «Versión 0.NN · dd mmm aaaa»). Súbela en cada entrega.
- Los módulos posteriores sobrescriben funciones anteriores del mismo archivo; busca la última definición antes de editar.
- Eventos: `click → H[data-a]`, `change → C[data-f]` (si devuelve `false` no se repinta), `input → I[data-i]`.
- La versión 0.75 fusiona la base de Noemí con las fichas técnicas y la lista de presupuestos de Pablo.

## Supabase (proyecto `fachadas-gestion`, región eu-west-1)
- Tablas: proveedores, articulos, articulo_precios, estudios, panos, huecos, clientes, obras, informes, documentos, estudio_articulos, estudio_datos_faltan, perfiles.
- Rol: `app_metadata.rol` del usuario (`admin`, `oficina`, `tecnico`). Las políticas RLS usan `es_oficina()` y `es_admin()`. Un usuario sin rol no ve datos.
- Alta de usuario: crear en Authentication, poner `rol` en sus metadatos y una fila en `perfiles`. Tiene que volver a iniciar sesión.
- La clave pública (publishable) va en el HTML; nunca pongas aquí claves `secret` ni `service_role`.
- Sincroniza hoy: proveedores, catálogo con precios, estudios con paños y huecos.
- Solo en el navegador (pendiente de migrar): presupuestos, clientes, obras, almacén y fichas técnicas (PDF en IndexedDB).

## Reglas de trabajo de Noemí
- Respuestas breves, en español. No borrar funciones existentes salvo que lo pida.
- Entrada de datos fácil y atractiva. 3D por defecto en estilo «Líneas». Tipografía fija.
- Sin estética de IA, neones ni iconos decorativos. Quitar textos superfluos.
- Pantallas con 3D sin scroll. Nivel de detalle de arquitecto experto. Ser honesto con las limitaciones.
- Verificar siempre la versión entregada. Hacer commit antes de cambios grandes.

## Pendiente
1. Migrar a Supabase: presupuestos, clientes, obras, almacén y fichas técnicas (PDFs en Storage + tabla `documentos`).
2. Publicar la app en una dirección web única para que todos usen la misma versión.
3. Aviso cuando otro usuario haya modificado el mismo estudio.
4. Anotaciones sobre el 3D, detalles ampliados con leyenda, paleta gris de secciones, líneas 3D más limpias.
