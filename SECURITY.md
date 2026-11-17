# Seguridad y revisión técnica

Esta guía corresponde a **Qverse 0.3.26 (31)** y al commit de compilación `ed1736d38c42023ea8a36e1bfa21312ff56d4e8a`. Las rutas indicadas están dentro del código fuente de esa beta.

## Controles de la billetera

| Control | Implementación |
| --- | --- |
| Generación de claves | La app usa el generador criptográfico de iOS para crear claves. Al importar, valida el WIF y deriva la dirección localmente. |
| Protección del WIF | Cifrado autenticado AES-256-GCM, ligado al registro de su cuenta. El Llavero usa `kSecAttrAccessibleWhenPasscodeSetThisDeviceOnly`, `.userPresence` y la sincronización desactivada en entradas nuevas. |
| Contraseña y biometría | El verificador de la contraseña local se deriva con PBKDF2-HMAC-SHA256. Face ID o Touch ID son opcionales para desbloquear. La lectura del WIF para exportar o firmar usa la autorización del sistema. |
| Sesión | Bloqueo manual y al alcanzar diez minutos de inactividad o en segundo plano. Al salir de primer plano, la app cubre su contenido y limpia los campos sensibles. |
| Revisión de envíos | La app verifica la red y las salidas, presenta el destinatario, el importe y la comisión, y construye y firma la transacción en el iPhone. |
| Resultado de un envío | La app calcula el identificador de la transacción en local y lo contrasta con la respuesta. Si el resultado es incierto, conserva las salidas reservadas y evita reenviar automáticamente. |

## Por dónde empezar la revisión

1. Revisa el almacenamiento y la autorización en `ios-beta/Sources/QverseRegtest/KeychainVault.swift`.
2. Sigue la creación, recuperación y firma en `ios-beta/Sources/QverseRegtest/RegtestWallet.swift`.
3. Revisa los datos que salen por red y la lógica de transmisión en `ios-beta/Sources/QverseRegtest/PublicChainClient.swift`.
4. Contrasta los casos de prueba en `ios-beta/Tests/QverseRegtestTests/PublicChainSendTests.swift` y las pruebas de interfaz en `ios-beta/UITests/WalletNavigationTests.swift`.

## Estado de verificación

- La beta pasó las pruebas Swift de recepción y envío, y el flujo del formulario de envío en el simulador de iPhone.
- La firma de referencia de dos entradas se verificó con OpenSSL. El cliente Swift de la beta 0.3.24 (27) también completó el recorrido de envío y confirmación en un nodo Qubitcoin regtest aislado.
- Apple procesó la compilación y la asignó al grupo interno de TestFlight.
- Siguen pendientes la auditoría independiente y las pruebas físicas de recuperación, biometría, cámara y envío. Haz las pruebas de fondos en regtest con claves desechables.

Si encuentras un problema, compártelo en privado con la persona que te dio acceso a la beta. Indica el commit, la pantalla o el archivo afectado y los pasos para reproducirlo con datos de prueba. Mantén fuera del informe las claves reales, contraseñas y copias de seguridad.
