# Control Remoto Web para TV (multimarca, por WiFi)

Página con botones, números, touchpad y teclado que controla tu TV desde el celular, en la misma red WiFi.

## Marcas soportadas

| Marca / sistema | Cómo se conecta | Primera vez |
|---|---|---|
| **Samsung** (Tizen, 2016+) | WebSocket 8002/8001 | Aceptar "Permitir" en la TV |
| **LG** (webOS) | WebSocket 3000/3001 | Aceptar el permiso en la TV |
| **Android TV / Google TV** (Sony, TCL, Hisense, Philips, Xiaomi, Panasonic, Sharp, Nvidia Shield…) | Android TV Remote v2 (puertos 6466/6467) | La TV muestra un código; lo escribes en la página |
| **Roku** (y TVs con Roku OS: TCL, Hisense, Philips…) | HTTP 8060 | Ajustes → Sistema → Config. avanzada → Control por apps móviles → "Permisivo" |
| **Sony Bravia** (IP Control) | HTTP 80 | Activar Control IP y definir una clave PSK en la TV |

No se puede garantizar "todas las marcas": cada fabricante usa su propio protocolo. Esto cubre la gran mayoría de las TVs actuales. Las TVs sin WiFi/red, o muy antiguas, solo se controlan con infrarrojo (hace falta un emisor IR).

## Instalar y usar
1. Instala Node.js 18 o superior (https://nodejs.org) en una PC, laptop o Raspberry conectada al mismo WiFi que la TV.
2. En esta carpeta: `npm install` y luego `npm start`.
3. La consola muestra una dirección como `http://192.168.1.20:3000`. Ábrela en el navegador del celular.
4. Ve a **Ajustes** → **Buscar TVs en mi WiFi**, toca tu TV y acepta el permiso/código que pida. (También puedes escribir la IP a mano.)

Tip: en el celular, menú del navegador → "Añadir a pantalla de inicio" para usarla como app. La próxima vez reconecta sola a la última TV.

## Si no conecta
- TV y servidor en el mismo WiFi (no "red de invitados"); la TV encendida (en espera la mayoría no responde).
- Samsung: Ajustes → General → Administrador de dispositivos externos → Administrador de conexión de dispositivos → permitir.
- Android TV: si pide código y no aparece, apaga y enciende la TV y vuelve a conectar.
- Sony: Ajustes → Red → Red doméstica → Control IP → Autenticación "Normal y clave precompartida".

## Qué funciona en cada marca
- **Puntero (flechita) del touchpad:** Samsung y LG. En las demás se usa el modo Flechas (deslizar = flechas, tocar = OK), que funciona en todas.
- **Teclado:** Samsung y LG escriben texto directo; Android TV y Roku mandan letra por letra; Sony no tiene entrada de texto.
- **Encender desde apagado:** casi ninguna TV responde por WiFi cuando está totalmente apagada (Roku TV sí). El botón ⏻ la apaga/enciende si está en espera.
- Si una tecla no existe en tu marca, la página avisa.

## Seguridad
El servidor no tiene contraseña: cualquiera en tu WiFi que abra la dirección puede controlar la TV. Úsalo en tu red de casa y solo acepta IPs locales. Los permisos guardados (tokens) quedan en `tv-data.json`.
