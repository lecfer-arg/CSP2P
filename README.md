# Club Satoshi · P2P

Web para comprar entre 1 y 10 dólares en satoshis a vendedores del Club Satoshi, con panel para vendedores.

## Probarla ya (modo demo)

Con `FIREBASE_CONFIG = null` (como viene), la web funciona en **modo demo**: todo se guarda solo en tu navegador.

1. Subí `index.html` a un repositorio de GitHub.
2. En el repo: **Settings → Pages → Branch: main / (root) → Save**.
3. Abrí la URL que te da GitHub (`https://TU-USUARIO.github.io/TU-REPO/`).
4. En una pestaña tocá **"Soy vendedor"**, cargá tus datos, guardá, habilitate en Administración y activá el interruptor.
5. En otra pestaña hacé de comprador. Los pedidos aparecen en la pestaña del vendedor.

> En modo demo cada navegador tiene sus propios datos: no sirve para probar entre varios celulares.

## Usarla entre varias personas (Firebase, gratis)

1. Entrá a https://console.firebase.google.com y creá un proyecto.
2. **Build → Firestore Database → Create database** (modo producción, ubicación `southamerica-east1`).
3. **Build → Authentication → Get started → Google → Enable.**
4. **Authentication → Settings → Authorized domains → Add domain:** `TU-USUARIO.github.io`.
5. **Project settings (⚙️) → Your apps → Web (`</>`)** → registrá la app y copiá el objeto `firebaseConfig`.
6. En `index.html`, pegalo en `FIREBASE_CONFIG` y poné tu email en `ADMIN_EMAILS`.
7. En **Firestore → Rules**, pegá el contenido de `firestore.rules` (con tu email) y publicá.
8. Subí el `index.html` actualizado a GitHub.

Cada vendedor entra con **"Soy vendedor" → Ingresar con Google**, carga sus datos, y el administrador lo habilita.

## Notas

- **Modo prueba:** al principio del código está `MODO_PRUEBA = true`, que agrega un vendedor ficticio siempre online que responde solo. Sirve para recorrer todas las pantallas. Ponelo en `false` antes de usar la web de verdad.

- **Cotización:** se toma en vivo de Binance (BTC/USDT) y CriptoYa (dólar blue + 3%) cada 60 segundos. Si alguna no responde, se usan valores de respaldo.
- **Avisos al vendedor:** el panel suena y vibra con cada pedido nuevo solo mientras está abierto.
- **Versión de prueba:** los datos de cobro y las facturas Lightning quedan visibles para cualquiera que lea la base. Antes de usarla con el público conviene mover la asignación de vendedores a un servidor.
