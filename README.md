# Manual de Instalación y Ejecución

## Requisitos

Para ejecutar este programa, es necesario tener instalado **Java 21**. Puede descargar la versión correspondiente desde el siguiente enlace:

[Descargar Java 21](https://adoptium.net/es/temurin/releases/)

## Descarga del Programa

El programa se encuentra disponible en este repositorio en el archivo `dist.zip`. Puede descargarlo desde el siguiente enlace:

[Descargar dist.zip](./dist.zip)

## Configuración

Antes de ejecutar el programa, es necesario personalizar el archivo `configuracion.config` con los parámetros específicos del sitio. Los siguientes parámetros son obligatorios:

- `sitename`: Nombre del sitio donde se instalará el sistema.
- `license`: Licencia específica del número de serie del lector RFID.

A continuación, se describe el resto de los parámetros de configuración:

### Parámetros de Configuración

| Clave                | Descripción |
|----------------------|-------------|
| `lector.ip`         | Dirección IP del lector RFID. Requerida para la conexión. |
| `lector.session`    | Modo de sesión RFID (`0`: inmediato, `1`: 4s, `2`: infinito). |
| `logger.level`      | Nivel de registro (`INFO`, `DEBUG`, `ERROR`). |
| `lector.power`      | Potencia de transmisión en dBm (Máx: `31.5`, Mín: `10.5`). Este valor es un número de punto flotante, debe tener el formato XX.XX .Para `31.5`, debe estar en **PoE+**. |
| `lector.sensitivity` | Sensibilidad de recepción en dBm (ejemplo: `-70.0`). |
| `lector.rfmode`     | Configuración del modo RF (valor entero). |
| `lector.antenas`    | Lista de antenas habilitadas separadas por comas. |
| `sitename`          | Nombre del sitio para el reporte al endpoint. |
| `license`          | Licencia específica del número de serie del lector RFID. |
| `endpoint.url`     | URL para enviar datos mediante HTTP POST (debe comenzar con `http://` o `https://`). |

## Ejecución

Para ejecutar el programa, use el siguiente comando en la terminal:

```sh
java -noverify -jar Autotrafic-production.jar
```

## Funcionamiento

Durante su ejecución, el programa procesa las lecturas del lector RFID y sigue la siguiente lógica:

1. Detecta un folio.
2. Si el folio es válido, procede a leer el VIN.
3. Si el VIN es válido, envía los datos mediante un **POST** al **endpoint** configurado en `endpoint.url`.

## Licencia

Este software está protegido bajo una licencia **restrictiva**. **Solo el dueño del equipo puede utilizar este programa.** 

Este software es privativo y no puede ser copiado, distribuido, modificado ni usado por terceros sin autorización expresa del propietario. Su uso está limitado exclusivamente al equipo original para el cual fue adquirido y cualquier intento de redistribución o alteración del código fuente está estrictamente prohibido.

