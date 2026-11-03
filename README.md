# Diseño y configuración de una red LAN con VLAN | Cisco Packet Tracer

**Proyecto académico de ASIR · Planificación y Administración de Redes · ILERNA**

## Sobre el proyecto

En esta práctica diseñé y configuré en **Cisco Packet Tracer** la red local de un centro educativo ficticio formado por dos aulas de alumnos y una sala de profesorado.

Mi objetivo fue conectar los dispositivos de las tres salas, asignarles direcciones IPv4, configurar los switches y separar lógicamente los equipos mediante **VLAN 10** y **VLAN 20**. Antes de entregar la actividad comprobé personalmente la configuración y el funcionamiento del laboratorio.

## Tecnologías y conocimientos aplicados

- Cisco Packet Tracer y comandos de **Cisco IOS** desde la CLI.
- Diseño de redes LAN y conexiones **Ethernet/GigabitEthernet**.
- Asignación de direcciones **IPv4 estáticas** y máscaras de subred.
- Configuración de **VLAN**, puertos de acceso y enlaces troncales (*trunk*).
- Consulta del estado de las interfaces de red.

## 1. Diseño de la topología

Organicé la red en tres salas y conecté los switches entre sí mediante enlaces GigabitEthernet:

| Sala | Dispositivos conectados |
| --- | --- |
| Aula 1 | 3 PCs y 1 portátil |
| Aula 2 | 3 PCs y 1 portátil |
| Profesorado | 2 portátiles |

En total utilicé **3 switches, 6 PCs y 4 portátiles**. Cada sala tiene su propio switch.

![Topología de las tres salas](capturas/01-topologia-tres-aulas.png)

Para revisar las interfaces de uno de los switches utilicé el comando:

```text
show ip interface brief
```

![Estado de las interfaces del switch](capturas/02-estado-interfaces-switch.png)

## 2. Configuración del direccionamiento IPv4

Asigné direcciones estáticas según el tipo de dispositivo:

| Dispositivos | Red IPv4 | Máscara |
| --- | --- | --- |
| PCs de escritorio | `192.168.10.0/24` | `255.255.255.0` |
| Portátiles | `192.168.20.0/24` | `255.255.255.0` |

Estos son dos ejemplos de la configuración que realicé:

**PC — `192.168.10.10`**

![Configuración IP de un PC](capturas/04-ip-pc-red10.png)

**Portátil — `192.168.20.10`**

![Configuración IP de un portátil](capturas/03-ip-portatil-red20.png)

También asigné nombres identificativos a los equipos para reconocerlos fácilmente en el mapa lógico.

![Topología con equipos identificados](capturas/05-topologia-equipos-renombrados.png)

## 3. Configuración de VLAN y switches

Configuré dos VLAN para separar los equipos por tipo:

- **VLAN 10:** equipos de escritorio.
- **VLAN 20:** portátiles.

Asigné los puertos de conexión de los dispositivos finales en **modo acceso** y configuré los enlaces entre switches en **modo troncal**, siguiendo los requisitos de la actividad.

Para administrar los switches trabajé desde la CLI de Cisco IOS. Entre los comandos empleados en la actividad están:

```text
Switch> enable
Switch# configure terminal
Switch(config)# hostname Sala1Apellido
Sala1Apellido(config)# interface GigabitEthernet0/1
Sala1Apellido(config-if)# switchport mode trunk
```

*El nombre `Sala1Apellido` es el ejemplo mostrado en el ejercicio; la configuración y los nombres del laboratorio se pueden consultar en el archivo `.pkt`.*

![Comandos de configuración del enlace troncal documentados en la PAC](capturas/06-comandos-troncal-ejercicio.png)

## 4. Comprobaciones realizadas

Antes de entregar la PAC revisé personalmente la topología, la asignación de direcciones IPv4, las conexiones de los dispositivos y la configuración de VLAN y enlaces troncales en Packet Tracer.

Las capturas incluidas muestran parte de esas comprobaciones, aunque **no conservé imágenes de todas las salidas de comandos**. Por ello adjunto también el archivo original `.pkt`, donde puede examinarse la configuración del laboratorio.

La práctica se centró en la **conmutación y segmentación de la LAN**. No configuré enrutamiento entre VLAN: el router mencionado en el enunciado quedaba fuera del alcance del ejercicio.

## 5. Archivo original de Packet Tracer

📁 **[Abrir o descargar el proyecto `.pkt`](packet-tracer/ASIR_Eduardo_Medialdea.pkt)**

Se necesita **Cisco Packet Tracer** para abrir el archivo y revisar la topología y las configuraciones. Para inspeccionar los switches también pueden utilizarse comandos como:

```text
show vlan brief
show interfaces trunk
show ip interface brief
```

*Estos comandos son opciones para revisar el proyecto; no todos aparecen documentados en las capturas adjuntas.*

## 6. Qué aprendí

Esta práctica me ayudó a afianzar el diseño de redes LAN, el direccionamiento IPv4 y la configuración de switches con Cisco IOS. También me permitió comprender mejor cómo las VLAN separan lógicamente los dispositivos y cómo los enlaces troncales transportan las VLAN entre switches.

Considero que estos conocimientos son una base importante para seguir formándome en **administración de redes y ciberseguridad**.

## Autor

**Eduardo Medialdea Dominguez**  
Estudiante de segundo curso de **Administración de Sistemas Informáticos en Red (ASIR)** — ILERNA.

*Este repositorio recoge mi trabajo en un entorno de simulación académica. Las capturas proceden de mi PAC y el archivo `.pkt` corresponde a la práctica entregada.*
