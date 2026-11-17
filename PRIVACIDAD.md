# Privacidad de Qverse Mobile

Esta información describe la app para iPhone **0.3.26 (31)**. Una clave WIF da acceso a la billetera que representa. La dirección pública sirve para recibir QTC y consultar movimientos.

## Qué guarda el iPhone

| Dato | Dónde se guarda |
| --- | --- |
| Claves WIF | En el Llavero de iOS, cifradas con AES-GCM y vinculadas al dispositivo. Las entradas nuevas usan acceso con presencia del usuario y llevan desactivada la sincronización con el Llavero de iCloud. |
| Contraseña de la app | Se guarda un verificador derivado de la contraseña con PBKDF2 y una sal aleatoria en el Llavero. |
| Preferencias | Ajustes locales de la app, como idioma, apariencia y preferencias de desbloqueo. |
| Saldos consultados y recibos de envío | Archivos locales con protección de datos de iOS. Contienen información pública de la billetera y el estado de las operaciones. |

## Qué datos usa la red

| Función | Datos enviados |
| --- | --- |
| Consultar Qubitcoin | El explorador recibe direcciones públicas o identificadores de transacciones y bloques que necesita consultar. |
| Enviar QTC | El servicio de Qubitcoin recibe la transacción firmada en el iPhone para transmitirla a la red. |
| Cotización y gráfica | CoinGecko y CoinPaprika reciben solicitudes de cotización e histórico de QTC/USD, sin direcciones de billetera. |
| Minería | La app consulta estadísticas de la pool. Si abres el panel de seguimiento de una dirección, el enlace incluye la dirección pública seleccionada. |
| Modo de pruebas | Si configuras un nodo regtest, la app envía las consultas RPC y sus credenciales a ese nodo. |

El flujo de red de la billetera mantiene la clave WIF y la contraseña de la app en el dispositivo. Los proveedores pueden ver datos técnicos de la conexión, como la dirección IP.

## Cámara y copia de seguridad

El iPhone solicita permiso de cámara cuando escaneas un QR para rellenar el destinatario. La lectura del QR se hace en el dispositivo. El QR de recepción contiene tu dirección pública y se genera localmente.

Para ver o copiar el WIF, la app pide autenticación del dispositivo. Si lo copias, queda temporalmente en el portapapeles del iPhone con caducidad de dos minutos. Si lo pegas en otra app o guardas una copia fuera de Qverse Mobile, esa copia pasa a depender de dónde y cómo la guardes.

Las claves del Llavero están ligadas al iPhone. Para recuperar una billetera en otro dispositivo, conserva tu propio respaldo del WIF y mantenlo en privado. [Protección de los ítems del Llavero](https://developer.apple.com/documentation/localauthentication/accessing-keychain-items-with-face-id-or-touch-id)

Cuando se usa Face ID o Touch ID, iOS comprueba la identidad y la app recibe el resultado de la autenticación. [Autenticación local de Apple](https://developer.apple.com/documentation/localauthentication/accessing-keychain-items-with-face-id-or-touch-id)
