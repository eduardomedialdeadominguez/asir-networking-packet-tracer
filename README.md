# Diseño de red de un centro educativo | Cisco Packet Tracer

**Proyecto académico de ASIR · Planificación y Administración de Redes**

## Resumen

Diseño de una topología de red simulada para un centro educativo compuesto por tres salas: dos aulas de alumnos y una sala de profesorado. El escenario incluye **3 switches**, **6 equipos de escritorio** y **4 portátiles**, con interconexiones GigabitEthernet entre switches. El proyecto original se conserva en formato `.pkt` para poder abrirlo en Cisco Packet Tracer.

> **Verificación del laboratorio:** antes de entregar la PAC, comprobé personalmente las configuraciones realizadas en Packet Tracer, incluidas las VLAN y los enlaces troncales. Las capturas seleccionadas ilustran parte del proceso, pero no contienen la salida de todos los comandos de verificación. El fichero `.pkt` permite revisar el diseño y sus configuraciones.

## Tecnologías y conceptos

- Cisco Packet Tracer y configuración mediante CLI Cisco IOS.
- Diseño de topologías LAN y conexiones Ethernet/GigabitEthernet.
- Direccionamiento IPv4 estático y máscaras de subred.
- Segmentación lógica configurada con **VLAN 10** (equipos de escritorio) y **VLAN 20** (portátiles), de acuerdo con la PAC.
- Configuración de puertos de acceso para los equipos finales y enlaces troncales entre switches.

## Escenario de red

| Elemento | Cantidad | Función |
|---|---:|---|
| Switches | 3 | Uno por sala, unidos mediante enlaces GigabitEthernet |
| PCs | 6 | Tres equipos de escritorio en cada una de las dos aulas de alumnos |
| Portátiles | 4 | Uno en cada aula de alumnos y dos en la sala de profesorado |

![Topología general](capturas/01-topologia-tres-aulas.png)

## Evidencias documentadas

### 1. Topología y estado de interfaces

En las capturas se observa el diseño de los tres grupos de equipos, sus conexiones a los switches y la ejecución del comando `show ip interface brief` en uno de ellos.

![Comprobación de interfaces del switch](capturas/02-estado-interfaces-switch.png)

### 2. Direccionamiento estático de los equipos

La actividad establece dos rangos IPv4: **192.168.10.0/24** para los PCs y **192.168.20.0/24** para los portátiles. Las capturas muestran, como ejemplo:

- PC: `192.168.10.10 / 255.255.255.0`
- Portátil: `192.168.20.10 / 255.255.255.0`

![IP configurada en un PC](capturas/04-ip-pc-red10.png)

![IP configurada en un portátil](capturas/03-ip-portatil-red20.png)

### 3. Nombres de los dispositivos

La PAC documenta la identificación de PCs y portátiles y la disposición de los switches en el mapa lógico.

![Topología con nombres](capturas/05-topologia-equipos-renombrados.png)

### 4. Configuración de los switches y enlaces troncales

```text
Switch> enable
Switch# configure terminal
Switch(config)# hostname Sala1Apellido
Sala1Apellido(config)# interface GigabitEthernet0/1
Sala1Apellido(config-if)# switchport mode trunk
```

La secuencia recoge los comandos de configuración del modo troncal documentados en la PAC. Según la comprobación que realicé antes de la entrega, esta configuración formaba parte del laboratorio terminado. La imagen muestra los comandos escritos en la actividad, no la salida de verificación del switch.

![Comandos abordados en la PAC](capturas/06-comandos-troncal-ejercicio.png)

## Archivo de Packet Tracer

[Descargar el diseño `.pkt`](packet-tracer/ASIR_Eduardo_Medialdea.pkt)

Abrirlo con una versión compatible de Cisco Packet Tracer. Para reproducir o auditar la comprobación se pueden usar `show vlan brief` y `show interfaces trunk` en cada switch, así como pruebas de conectividad entre equipos de la misma VLAN. No se afirma que exista comunicación entre VLAN distintas sin un dispositivo que realice enrutamiento.

## Alcance de la documentación

- La configuración de las VLAN y los enlaces troncales fue comprobada por el autor antes de la entrega; las capturas disponibles no muestran todas las salidas de verificación.
- El archivo `.pkt` se adjunta tal como fue entregado. Esta documentación se basa en la PAC, las capturas y la confirmación del autor, **sin una auditoría independiente del archivo en Packet Tracer**.

## Autor

Eduardo Medialdea Dominguez · Estudiante de ASIR en ILERNA.

*Repositorio creado a partir de un laboratorio académico. Las capturas se han recortado para mostrar únicamente evidencias relevantes, sin publicar el enunciado completo de la actividad.*
