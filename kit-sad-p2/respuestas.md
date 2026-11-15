# Respuestas · Práctica 2 · Bodegas Atlántico

> Rellena este fichero en tu ordenador. Va en la entrega (`./lab.sh entregar`) y en la defensa te pueden preguntar por él.

## Bloque A · Piensa como un atacante (nmap)

Desde la calle: `./lab.sh cliente` y dentro `nmap -Pn -p 22,80,443,5432,8080 198.51.100.254`. Pega la salida:

```text
(pega aquí la salida de nmap)
```
Starting Nmap 7.95 ( https://nmap.org ) at 2026-11-08 18:57 UTC
Nmap scan report for sad-p2-fw.sad-p2_calle (198.51.100.254)
Host is up (0.000067s latency).

PORT     STATE    SERVICE
22/tcp   filtered ssh
80/tcp   open     http
443/tcp  open     https
5432/tcp filtered postgresql
8080/tcp filtered http-proxy
MAC Address: C6:FE:D0:C4:0E:4D (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 1.28 seconds

## Bloque A · El contador

Después de `./lab.sh comprobar`, mira `./lab.sh ver`. ¿Cuántos paquetes lleva el contador de A6? ¿Quién los ha mandado?

Lleva 6 paquetes mandados 360bytes y los ha enviado la red de la tienda hacia las oficinas.
>

## Bloque B · La prueba del cifrado

En el firewall (`./lab.sh fw`): `tcpdump -ni wan host 198.51.100.62 -c 6`. Mientras, en otra terminal, el comercial
(`./lab.sh comercial`) hace `curl http://172.16.10.20:8080`. Pega lo que sale en el firewall:

```text
listening on wan, link-type EN10MB (Ethernet), snapshot length 262144 bytes
14:09:00.420809 IP 198.51.100.62.48686 > 198.51.100.254.51820: UDP, length 32
14:09:25.508792 IP 198.51.100.62.48686 > 198.51.100.254.51820: UDP, length 32
14:09:30.628766 ARP, Request who-has 198.51.100.254 tell 198.51.100.62, length 28
14:09:30.628786 ARP, Reply 198.51.100.254 is-at ce:3f:b0:2d:c1:cc, length 28
14:09:50.596788 IP 198.51.100.62.48686 > 198.51.100.254.51820: UDP, length 32
14:09:50.596957 IP 198.51.100.62.48686 > 198.51.100.254.51820: UDP, length 148
6 packets captured
8 packets received by filter
0 packets dropped by kernel


```

En dos líneas: ¿qué se ve por la calle y qué NO se ve?

>

## Bloque C · Para la defensa (C4)

Del **mismo ataque** (la inyección a la web): ¿qué ve el vigilante de la red (el IDS) y qué ve el portero de la web? ¿Por
qué hacen falta los dos?

>

## Bloque D · La nota del servidor (D0 y D4)

Nota del análisis **antes** de bastionar (D0):

>

Nota **después** (D4). ¿Por qué no llega a 100? ¿Significa que el servidor sigue inseguro? Comenta un aviso que siga saliendo.

>
