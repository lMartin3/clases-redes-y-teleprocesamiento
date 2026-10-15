# Glosario · VLANs, «Un muelle, cinco cargas»

Los términos de cada escena del deck. Es lo mismo que muestra la tecla **N** en `Un muelle, cinco cargas.html`.

## 01 · Un muelle, cinco cargas

- **VLAN (Virtual LAN):** red local lógica: separa equipos conectados al mismo hardware como si estuvieran en switches distintos.
- **Trama:** unidad de datos de capa 2 (Ethernet): lleva MAC de destino, MAC de origen, tipo y datos.

## 02 · Todo en el mismo muelle

- **Dominio de broadcast:** conjunto de equipos que recibe una misma trama de broadcast. Un switch sin VLANs es un solo dominio.
- **Broadcast:** trama dirigida a todos: MAC de destino ff:ff:ff:ff:ff:ff.
- **ARP:** protocolo que averigua qué MAC tiene una IP de la misma red; la pregunta sale por broadcast.
- **Red plana:** una sola red sin segmentar: cualquier equipo alcanza a cualquier otro.

## 03 · Cinco redes, un solo equipo

- **IEEE 802.1Q:** estándar que define las VLANs y la etiqueta que llevan las tramas en un trunk.
- **VLAN ID (VID):** número de 12 bits que identifica la VLAN: de 1 a 4094 (0 y 4095 reservados).
- **Interfaz VLAN:** interfaz lógica del router sobre el bridge, una por VLAN (vlan-admin-10, vlan-server-20, …).

## 04 · Quién va a cada playa

- **Segmentación:** dividir la red en zonas según función o confianza, para limitar qué puede alcanzar cada equipo.
- **Iniciar una conexión:** mandar el primer paquete de una conversación; la política dice qué VLAN puede hacerlo hacia cuál.
- **Address list:** en RouterOS, lista con nombre de direcciones IP que se usa en reglas de firewall.

## 05 · Access y trunk

- **Puerto access:** puerto de una sola VLAN; las tramas entran y salen sin etiqueta (untagged).
- **Puerto trunk:** puerto que lleva varias VLANs; cada trama viaja con su etiqueta 802.1Q (tagged).
- **Etiqueta 802.1Q:** 4 bytes entre la MAC de origen y el EtherType: TPID, PCP, DEI y VID.
- **TPID:** Tag Protocol Identifier, 16 bits con el valor 0x8100: avisa que la trama está etiquetada.
- **PCP / DEI:** PCP: 3 bits de prioridad. DEI: 1 bit que marca la trama como descartable ante congestión.
- **VLAN nativa:** la que viaja sin etiqueta por un trunk; en RouterOS, la PVID del puerto.

## 06 · La libreta de la grúa

- **Dirección MAC:** identificador de 48 bits de una interfaz de red, escrito como 6 pares hexadecimales.
- **Tabla MAC (bridge › hosts):** lo que aprendió el switch: qué MAC está detrás de qué puerto, por VLAN.
- **Inundación (flooding):** si el destino no está en la tabla, la trama sale por todos los puertos de esa VLAN.
- **Aging:** tiempo después del cual una entrada de la tabla vence si el equipo no volvió a hablar.

## 07 · La entrada a cada playa

- **Bridge:** en RouterOS, el switch por software que une varios puertos en un mismo segmento.
- **VLAN filtering:** opción del bridge que hace cumplir la configuración de VLANs; sin ella no se aplican.
- **PVID:** Port VLAN ID: la VLAN que el puerto le asigna a una trama que llega sin etiqueta.
- **Frame types:** qué tramas acepta un puerto: admit-all, admit-only-vlan-tagged o admit-only-untagged-and-priority-tagged.
- **Ingress filtering:** descarta en la entrada las tramas de VLANs a las que el puerto no pertenece.
- **Priority-tagged:** trama con etiqueta 802.1Q y VID 0: solo lleva prioridad; se trata como sin etiqueta.
- **VLAN hopping:** ataque que intenta meter tramas en otra VLAN, por ejemplo mandándolas ya etiquetadas.

## 08 · Vecinos que no se ven

- **Horizon:** valor de un puerto del bridge: no se reenvían tramas entre puertos con el mismo horizon.
- **Client isolation:** opción del AP que impide que dos clientes Wi-Fi se hablen entre sí.
- **Último eslabón:** el punto donde se conecta el cliente (puerto, AP u otro switch): ahí se aplica el aislamiento.

## 09 · La grúa trabaja sola

- **Hardware offloading:** el chip de switch reenvía las tramas entre puertos sin pasar por la CPU del router.
- **Flag «H»:** en bridge › ports, indica que el puerto está offloaded por hardware.
- **iperf3:** herramienta que mide el ancho de banda entre dos equipos (cliente y servidor).

## 10 · Una subred por VLAN

- **Subred:** rango de direcciones IP que comparten el prefijo de red.
- **CIDR / prefijo:** notación /n: cuántos bits son de red. /24 = máscara 255.255.255.0.
- **Dirección de red y de broadcast:** la primera (.0) y la última (.255) de una /24; no se asignan a equipos.
- **Gateway:** dirección del router en la subred; a ella va todo lo que tiene destino fuera de la red.
- **Ruta DAC:** en RouterOS: dinámica, activa y conectada; aparece sola al asignar una dirección a una interfaz.

## 11 · La puerta de servicio

- **Puerto de administración:** puerto sacado del bridge, con su propia red, para gestionar el router aunque fallen las VLANs.
- **WebFig:** interfaz web de configuración de RouterOS.
- **IP fija (estática):** dirección configurada a mano en el equipo, sin DHCP.

## 12 · Cada uno recibe su lugar

- **DHCP:** protocolo que entrega dirección, máscara, gateway y DNS a los equipos que se conectan.
- **DORA:** los cuatro mensajes: Discover (broadcast), Offer, Request y Ack.
- **Pool:** rango de direcciones que el servidor DHCP puede repartir (ej. 192.168.30.11–192.168.30.254).
- **Lease:** tiempo por el que se presta una dirección; el cliente la renueva antes de que venza.

## 13 · Para cruzar, por la aduana

- **Ruteo entre VLANs:** pasar tráfico de una VLAN a otra a través del router (capa 3).
- **Router-on-a-stick:** un solo enlace trunk entre switch y router, con una interfaz lógica por VLAN.
- **Gateway por defecto:** adonde un equipo manda lo que no es de su red; en cada VLAN, la .1 del router.

## 14 · Quién abre la conversación

- **Connection tracking:** tabla del firewall con las conexiones vistas y su estado.
- **new:** primer paquete de una conexión.
- **established:** paquetes de una conexión ya abierta, en cualquiera de los dos sentidos.
- **related:** conexión asociada a otra existente (por ejemplo, un ICMP de error).
- **invalid:** paquete que no corresponde a ninguna conexión válida; se descarta.

## 15 · El libro de la aduana

- **Cadena (chain):** lista de reglas que se evalúa en orden: input (hacia el router), forward (lo atraviesa), output (sale del router).
- **Regla:** condiciones (interfaces, direcciones, estado, puertos) más una acción.
- **accept / drop:** dejar pasar el paquete o descartarlo sin avisar.
- **Primera coincidencia:** gana la primera regla que coincide; por eso el orden importa.

## 16 · Una antena, varias redes

- **SSID:** nombre de una red Wi-Fi.
- **AP virtual:** red Wi-Fi adicional publicada por el mismo radio del access point.
- **VLAN mapping:** asociar un SSID a una VLAN: quien se conecta a ese SSID queda en esa VLAN.

## 17 · Todos salen con el mismo nombre

- **WAN:** la red de afuera (internet o la red del proveedor); en la guía, ether1 fuera del bridge.
- **DHCP client:** el router pide su propia dirección en la WAN.
- **Source NAT / masquerade:** el router reemplaza la IP privada de origen por la suya al salir; masquerade usa la IP que tenga la interfaz.
- **DNS:** sistema que traduce nombres de dominio a direcciones IP.
- **Caché DNS:** el router responde las consultas de la red y guarda las respuestas (allow-remote-requests).

## 18 · Lo que entra desde afuera

- **Destination NAT / port forward:** el router reenvía lo que llega a un puerto de su IP pública hacia un equipo interno.
- **DMZ:** zona separada donde viven los servicios expuestos a internet, aislada del resto de la red.
- **Proxy reverso:** servidor (NGINX, Caddy) que recibe los pedidos y los deriva a la app según el nombre pedido.
- **Registro A:** entrada DNS que asocia un nombre a una dirección IPv4.
- **403:** código HTTP de acceso prohibido.

## 19 · El muelle completo

- **RouterOS:** sistema operativo de los equipos MikroTik.
- **Capa 2 / capa 3:** capa 2: tramas y MAC dentro de una red (switch). Capa 3: paquetes IP entre redes (router).
