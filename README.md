# Qverse Mobile

**Billetera de Qubitcoin (QTC) para iPhone.** La app permite crear y recuperar billeteras, recibir QTC y firmar envíos desde el dispositivo.

[Privacidad y datos](PRIVACIDAD.md) · [Seguridad y revisión técnica](SECURITY.md) · [Extensión original de Qverse Wallet](https://github.com/QverseWallet/Qverse-Wallet)

## Qué incluye la app

| Apartado | Funciones |
| --- | --- |
| Billeteras | Creación e importación con clave WIF, gestión de varias cuentas y respaldo manual. |
| Recibir | Dirección pública y QR local, saldo confirmado e ingresos pendientes. |
| Enviar | Destinatario por texto o cámara, importe en QTC, selección de porcentaje, revisión de comisión y firma en el iPhone. |
| Actividad | Historial, estado de confirmación y acceso al explorador de Qubitcoin. |
| Mercado y minería | Cotización QTC/USD, gráfica, explorador, estadísticas de la pool y guía para equipos externos. |

## Las claves se guardan en el iPhone

Qverse Mobile es una billetera de **autocustodia**. La app crea o importa la clave WIF en el dispositivo, la cifra y la guarda en el **Llavero de iOS**. El Llavero exige el código del iPhone y autoriza las operaciones sensibles mediante los controles de autenticación del sistema. El usuario puede elegir Face ID o Touch ID para desbloquear la app cuando su dispositivo lo permite. [Cómo protege Apple el Llavero](https://support.apple.com/es-lamr/guide/security/secb0694df1a/web)

La firma se realiza en el iPhone. Para consultar la red se usan direcciones públicas y referencias de transacciones. Al enviar, el explorador recibe la transacción **ya firmada**. La clave WIF queda en el dispositivo, salvo las copias que el usuario decida guardar por su cuenta. [Qué datos utiliza la app](PRIVACIDAD.md)

## Estado de la beta

**Qverse 0.3.26 (31)** está disponible para el grupo interno de TestFlight. La compilación salió del commit `ed1736d38c42023ea8a36e1bfa21312ff56d4e8a` del repositorio de publicación.

El usuario de la beta confirmó el envío y la recepción de QTC en un iPhone físico. También pasaron las pruebas Swift y el recorrido de envío en simulador. Quedan pendientes la auditoría independiente y las pruebas físicas de recuperación, biometría y cámara. [Alcance de las pruebas](SECURITY.md#estado-de-verificación)

El código de ese commit y la invitación de TestFlight se entregan por separado a quien vaya a revisar o probar la beta.

## Proyecto original

Qverse Mobile adapta a iOS el trabajo de [Qverse Wallet](https://github.com/QverseWallet/Qverse-Wallet). La extensión original está publicada bajo licencia MIT. Esta página documenta la app móvil y su estado de verificación.
