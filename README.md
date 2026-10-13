# GNS3 Labs

Laboratorios de redes montados en GNS3, uno por carpeta. Cada laboratorio se termina y se documenta en un fin de semana: topología, plan de direccionamiento, configuraciones, pruebas y escenarios de averías con su diagnóstico.

Todo está hecho con software libre o gratuito (VyOS, FRRouting, Open vSwitch, OPNsense, contenedores Alpine/Debian), para que cualquiera pueda reproducirlo. Para los laboratorios de Active Directory se usa Windows Server en versión de evaluación.

## Estado

🚧 En preparación. El plan completo está en [ROADMAP.md](ROADMAP.md).

| Laboratorio | Tema | Estado |
|---|---|---|
| 00 | Preparación del entorno | En curso |
| 01 | Oficina con VLANs | Pendiente |
| 02 | Dominio Active Directory | Pendiente |
| 03 | Enrutamiento OSPF | Pendiente |
| 04 | VPN entre sedes | Pendiente |
| 05 | Firewall perimetral con OPNsense | Pendiente |
| 06 | Monitorización | Pendiente |
| 07 | BGP con dos proveedores | Pendiente |
| 08 | Automatización con Ansible | Pendiente |
| 09 | Migración a Proxmox | Pendiente |

## Entorno

- GNS3 server y GNS3 VM sobre VMware Workstation (Ryzen 7, 32 GB de RAM)
- Cliente GNS3 desde un portátil con Ubuntu

## Estructura de cada laboratorio

```
NN-nombre-del-lab/
├── README.md          # objetivo, topología y pruebas
├── diagrama.png
├── direccionamiento.md
├── configs/           # configuración exportada de cada equipo
├── averias.md         # síntomas, diagnóstico y solución
└── capturas/
```

Las imágenes de los equipos y los discos de las máquinas virtuales no se incluyen en el repositorio; cada laboratorio indica de dónde descargarlas.
