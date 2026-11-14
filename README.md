# SuperProductos

Tienda web estática de accesorios de cómputo para San Isidro, Lima. Está hecha con HTML, CSS y JavaScript sin proceso de compilación.

## Ejecutar

Abre `index.html` o sírvelo desde un servidor estático. El catálogo público usa productos de demostración hasta que se conecte Supabase.

## Conectar Supabase

Pulsa el engranaje e ingresa la Project URL y la publishable key (o la legacy anon key) desde **Project Settings → API Keys**. Nunca uses una `service_role` o secret key en el navegador. La conexión y la sesión se conservan solo en `sessionStorage` y se eliminan al cerrar la pestaña.

La aplicación usa las tablas `producto`, `vendedor` y `ventas` por defecto. El engranaje permite ajustar tablas y nombres de columnas.

## Auth y acceso a ventas

El catálogo y las páginas informativas son públicas. El área de ventas (`#ventas`) requiere una sesión Supabase: los usuarios pueden iniciar sesión o registrarse con correo y contraseña, y cerrar sesión desde la aplicación. Si el proyecto requiere confirmación de correo, el usuario debe confirmar antes de iniciar sesión. Configura el Site URL y los Redirect URLs del proyecto para el dominio donde se publica la aplicación.

El guard del navegador mejora el flujo de acceso, pero la seguridad de los datos debe aplicarse también en Postgres con RLS. Activa RLS y define políticas para `producto`, `vendedor` y `ventas` según los roles que pueden consultar o registrar operaciones. La app envía el access token del usuario para que RLS pueda evaluarlo. No se aplicaron políticas a una base remota porque no hay un proyecto Supabase conectado a esta sesión y el esquema real de tablas no está disponible; revisa el modelo antes de crear políticas.

## Esquema de ventas

La aplicación carga productos y vendedores tras iniciar sesión. Al grabar, inserta una fila por cada producto del carrito en `ventas`, con vendedor, producto, cantidad, precio unitario y total de línea. Si tu tabla requiere columnas adicionales o una estructura de cabecera y detalle, adapta el guardado y las políticas a ese esquema.

## Contacto

- San Isidro, Lima
- Teléfono y WhatsApp: +51 943 094 835
- Correo: joseestradatoledo0407@gmail.com
