---
proyecto: gns3-labs
repo: https://github.com/robertocmt13/gns3-labs
estado: en preparación
tags: [gns3, redes, portfolio]
---

# Roadmap — gns3-labs

Laboratorios de redes en GNS3, uno por carpeta, cada uno terminado y documentado en un fin de semana libre (8–12 horas). Solo software libre o gratuito, para que cualquiera pueda reproducirlos.

**Entorno:** GNS3 server + GNS3 VM en la torre (Ryzen 7, 32 GB) con VMware Workstation. Cliente GNS3 también desde el portátil.

---

## 00 · Preparación del entorno
*Antes del primer finde. 2–4 h.*

- [ ] Activar SVM Mode en la BIOS de la torre
- [ ] Desactivar Hyper-V, Plataforma de máquina virtual e Integridad de memoria en Windows
- [ ] Instalar VMware Workstation Pro
- [ ] Instalar GNS3 e importar la GNS3 VM en VMware
- [ ] Comprobar que la GNS3 VM tiene KVM disponible
- [ ] Descargar ISO de VyOS (rolling) y plantilla de Open vSwitch
- [x] Crear repo `gns3-labs` en GitHub con README, `.gitignore` (imágenes y discos fuera) y este roadmap
- [ ] Prueba mínima: dos contenedores Alpine se hacen ping a través de un VyOS

---

## 01 · Oficina pequeña con VLANs
*Dificultad: baja. 1 finde.*

- [ ] Topología: VyOS + Open vSwitch + clientes Alpine + nodo NAT
- [ ] Plan de direccionamiento: VLAN administración, usuarios e invitados
- [ ] Router-on-a-stick con subinterfaces
- [ ] DHCP por VLAN en el router
- [ ] NAT de salida a internet
- [ ] Firewall: invitados solo salen a internet, sin acceso a otras VLANs
- [ ] Averías: VLAN mal etiquetada, DHCP sin respuesta, falta ruta por defecto
- [ ] Documentación y publicación

---

## 02 · Dominio Active Directory
*Dificultad: media. 1 finde.*

- [ ] Windows Server (evaluación) como nodo VMware en GNS3
- [ ] Controlador de dominio con DNS integrado
- [ ] DHCP en Windows Server con relay desde el router
- [ ] OUs, usuarios y grupos por departamento (script PowerShell)
- [ ] GPOs: mapeo de unidad, fondo corporativo, restricciones básicas
- [ ] Cliente Windows unido al dominio
- [ ] Averías: el equipo no se une al dominio, una GPO no se aplica, DNS mal configurado en el cliente
- [ ] Documentación y publicación

---

## 03 · Enrutamiento dinámico con OSPF
*Dificultad: media. 1 finde.*

- [ ] Tres o cuatro routers VyOS/FRRouting con enlaces redundantes
- [ ] OSPF en área única y después con varias áreas
- [ ] Prueba de convergencia al tirar un enlace
- [ ] Averías: vecindad que no se forma (MTU, área, timers), red no anunciada
- [ ] Documentación y publicación

---

## 04 · VPN entre sedes
*Dificultad: media. 1 finde.*

- [ ] Sede central y sucursal conectadas por un "internet" simulado
- [ ] Túnel WireGuard entre sedes
- [ ] (Opcional) Mismo escenario con IPsec
- [ ] Rutas entre las redes internas de ambas sedes
- [ ] Averías: claves incorrectas, MTU, rutas que faltan
- [ ] Documentación y publicación

---

## 05 · Firewall perimetral con OPNsense
*Dificultad: media. 1 finde.*

- [ ] OPNsense con zonas LAN, DMZ y WAN
- [ ] Servidor web en la DMZ con port forwarding
- [ ] Reglas por zona y registro de tráfico bloqueado
- [ ] Averías: regla en el orden equivocado, NAT que no se aplica
- [ ] Documentación y publicación

---

## 06 · Monitorización
*Dificultad: media. 1 finde.*

- [ ] Zabbix o LibreNMS en contenedor
- [ ] SNMP en routers y switches
- [ ] Syslog centralizado
- [ ] Alertas de caída de enlace y de equipo
- [ ] Averías: SNMP sin respuesta, alerta que no salta
- [ ] Documentación y publicación

---

## 07 · BGP con dos proveedores
*Dificultad: alta. 1–2 findes.*

- [ ] Empresa con conexión a dos ISPs simulados
- [ ] eBGP con cada ISP y anuncio del prefijo propio
- [ ] Preferencia de salida (local preference) y failover
- [ ] Averías: sesión BGP caída, prefijo no anunciado
- [ ] Documentación y publicación

---

## 08 · Automatización con Ansible
*Dificultad: media. 1 finde.*

- [ ] Inventario con los equipos de un laboratorio anterior
- [ ] Playbook de backup de configuraciones
- [ ] Playbook de despliegue de una VLAN nueva
- [ ] Documentación y publicación

---

## 09 · Migración a Proxmox
*Cuando el portátil tenga Proxmox.*

- [ ] Instalar Proxmox en el portátil
- [ ] Migrar la GNS3 VM o instalar GNS3 server en una VM
- [ ] Documentar el proceso y las diferencias

---

## Checklist de cierre de cada laboratorio

- [ ] Diagrama de topología
- [ ] Plan de direccionamiento IP
- [ ] Configuraciones exportadas de todos los equipos
- [ ] Pruebas de funcionamiento con capturas
- [ ] Escenarios de averías: síntomas, diagnóstico y solución
- [ ] README de la carpeta
- [ ] Actualizar el README principal y este roadmap

## Estructura de cada carpeta

```
NN-nombre-del-lab/
├── README.md
├── diagrama.png
├── direccionamiento.md
├── configs/
├── averias.md
└── capturas/
```
