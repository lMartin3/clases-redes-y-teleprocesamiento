# Redes y Teleprocesamiento · clases

## VLANs · «Un muelle, cinco cargas» (jueves 15/10/2026, 18:00)

Clase teórica de VLANs sobre la red hogareña del plan de clase, antes de la práctica con el MikroTik.
Presentan Valentín Torassa Colombero, Martín Luraschi y Manuel Regiardo.

- **Para presentar:** abrí [`vlans/Un muelle, cinco cargas.html`](vlans/) en Firefox o Chrome. Funciona sin internet: las fuentes y las librerías están adentro.
- **Teclas:** → o espacio avanza, ← vuelve, **N** muestra el glosario de la escena y **F** pone pantalla completa. `#s5` en la URL abre la escena 5.
- **Glosario:** [`vlans/GLOSARIO.md`](vlans/GLOSARIO.md), los términos de cada escena con una definición corta.

| Escenas | Quién | Temas |
| --- | --- | --- |
| 1–12 | Valentín | red plana, qué es una VLAN, diseño, access y trunk, aprendizaje de MAC, filtrado en el bridge, aislamiento de clientes, hardware offloading, subredes, puertos de administración, DHCP |
| 13–15 | Martín | ruteo entre VLANs, estado de conexiones, firewall |
| 16–19 | Manuel | Wi-Fi (SSIDs y VLAN mapping), NAT y DNS, port forward, DMZ y proxy reverso, cierre |

La metáfora: un puerto. Cada contenedor es una trama y cada color, una VLAN. La grúa es el switch, la barcaza es el trunk, la aduana es el router con el firewall y el NAT, y la zona franca es la DMZ.

Los datos (VLANs 10, 20, 30, 40 y 100; interfaces `vlan-*`; subredes `192.168.X.0/24`; puertos `ether3`–`ether12`; puertos de administración `ether23` y `ether24`; pools y lease) salen del plan de clase y de la guía del router. Son de ejemplo, y así se marcan: las IPs de los hosts, los nombres de los SSID, la tabla de firewall (escrita con la política del plan) y `<dominio>`/`<proxy>`.

Ojo con la guía: en «bridge › VLANs», el paso 5 dice «puertos físicos como taggeados», pero los puertos access van como **untagged** (así lo muestra la captura).
