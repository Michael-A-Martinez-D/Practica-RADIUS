Enlace del video: https://youtu.be/K7sv36a3oyM

El propósito de este laboratorio es comprobar como el servicio RADIUS puede centralizar la autenticación, autorización y logs de los equipos de red con RADIUS (NPS y Active Directory), para que cada administrador entre con su propio usuario y solo tenga los permisos de su nivel.

## Versiones de los dispositivos

| Dispositivo | Imagen / Versión | Rol |
|-------------|------------------|-----|
| Router | Cisco IOL (versión: 15.7) | Cliente RADIUS, SSH |
| Switch | Cisco vIOS-L2 `viosl2-adventerprisek9-m.ssa.high_iron_20200929` (versión: 15.2) | Cliente RADIUS, SSH |
| Servidor | Windows Server 2022 (Standard, Desktop Experience) | Active Directory y NPS |
| PNetLab | versión: 4.2.10 | Plataforma de simulación |


## Direccionamiento VLSM - Infraestructura 3 (AAA con RADIUS)

Matricula: 2025-1410

Red base: `14.10.0.0/16` (últimos 4 dígitos de la matrícula)

| # | Segmento | Red | Máscara | Prefijo | Hosts | Rango útil | Broadcast |
|---|----------|-----|---------|---------|-------|------------|-----------|
| 1 | Gestión | 14.10.10.0 | 255.255.255.240 | /28 | 14 | 14.10.10.1 - 14.10.10.14 | 14.10.10.15 |

### Asignación de IPs

| Dispositivo | Interfaz | IP | Gateway |
|-------------|----------|----|---------|
| Servidor (AD + NPS) | Ethernet | 14.10.10.2/28 | 14.10.10.3 |
| Router (R1) | e0/0 | 14.10.10.3/28 | - |
| Switch (SW1) | Vlan1 | 14.10.10.4/28 | 14.10.10.3 |

---

## Topología

![Topología](imagenes/topologia.png)

---

## Active Directory

### Usuarios y grupos

![Usuarios y grupos](imagenes/UsuariosYGrupos.png)

### Miembros de cada grupo

![Usuarios grupo nivel 0](imagenes/Usuarios_grupo0.png)

![Usuarios grupo nivel 5](imagenes/Usuarios_grupo5.png)

![Usuarios grupo nivel 10](imagenes/Usuarios_grupo10.png)

---

## NPS

### Clientes RADIUS

![Clientes RADIUS](imagenes/Clientes_Radius.png)

### Directivas de red

![Directiva de red nivel 0](imagenes/DirectivaDeRed_nivel0.png)

![Directiva de red nivel 5](imagenes/DirectivaDeRed_nivel5.png)

![Directiva de red nivel 10](imagenes/DirectivaDeRed_nivel10.png)

---

## Pruebas

### Acceso por SSH al router (R1)

![SSH user_n0 - R1](imagenes/pruebas/ssh_usern0_R1.png)

![SSH user_n5 - R1](imagenes/pruebas/ssh_usern5_R1.png)

![SSH user_n10 - R1](imagenes/pruebas/ssh_usern10_R1.png)

### Acceso por SSH al switch (SW1)

![SSH user_n0 - SW1](imagenes/pruebas/ssh_usern0_SW1.png)

![SSH user_n5 - SW1](imagenes/pruebas/ssh_usern5_SW1.png)

![SSH user_n10 - SW1](imagenes/pruebas/ssh_usern10_SW1.png)

### Logs de autenticación y autorización

![show logging - R1](imagenes/pruebas/show_logging_R1.png)

![show logging - SW1](imagenes/pruebas/show_logging_SW1.png)

### Eventos en el servidor (NPS)

![Eventos](imagenes/pruebas/Eventos.png)
