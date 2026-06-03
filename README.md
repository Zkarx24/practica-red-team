# Práctica Red Team - Gabriel Gutiérrez

Este repositorio contiene la entrega de la **Práctica Red Team**, separada en dos memorias técnicas:

1. **Memoria_Practica_RedTeam_Lab_Gabriel_Gutierrez.pdf**
2. **Memoria_Practica_RedTeam_Recon_Gabriel_Gutierrez.pdf**

---

## 1. Red Team Lab

La memoria **Red Team Lab** documenta la construcción de un laboratorio interno basado en **Active Directory**, segmentación de red, pivoting y análisis de relaciones de privilegios.

### Contenido principal

* Preparación de un dominio Windows `lab.local`.
* Configuración de Windows Server 2019 como controlador de dominio `CD01`.
* Configuración de Windows 10 como estación de trabajo y máquina pivot.
* Validación de segmentación entre Kali, Windows 10 y CD01.
* Uso de **Chisel** para crear un túnel reverse SOCKS.
* Uso de **proxychains** para redirigir tráfico desde Kali hacia la red interna.
* Validación de acceso SMB y LDAP mediante **NetExec**.
* Recolección de información del dominio con **SharpHound**.
* Análisis de relaciones de privilegios con **BloodHound**.
* Identificación de una ruta de privilegios desde `GABO@LAB.LOCAL` hacia `BACKUP OPERATORS@LAB.LOCAL`.

### Hallazgo principal

Se identificó una delegación insegura de privilegios:

```text
GABO@LAB.LOCAL
  -> IT_BACKUP_OPERATORS@LAB.LOCAL
  -> BACKUP OPERATORS@LAB.LOCAL
```

Esta relación evidencia cómo una membresía indirecta puede otorgar acceso a grupos sensibles dentro de Active Directory.

---

## 2. Red Team Recon

La memoria **Red Team Recon** documenta un reconocimiento externo controlado sobre activos en scope del programa **Unico IDtech** en HackerOne.

### Contenido principal

* Definición de scope autorizado desde HackerOne.
* Creación de archivo `scope.txt` con activos incluidos en el alcance.
* Enumeración de subdominios con **subfinder**.
* Resolución DNS con **dnsx**.
* Detección de servicios HTTP/HTTPS vivos con **httpx**.
* Clasificación de códigos HTTP y tecnologías observadas.
* Escaneo controlado con **Nuclei**.
* Recolección de URLs con **Katana**.
* Extracción de archivos JavaScript.
* Filtrado de URLs interesantes para revisión manual posterior.

### Resultados principales

```text
Activos iniciales en scope: 14
Subdominios encontrados con subfinder: 192
Dominios únicos analizados: 198
Registros DNS obtenidos: 414
Hosts únicos que resuelven DNS: 133
URLs HTTP/HTTPS vivas: 123
URLs recolectadas con Katana: 3417
Archivos JavaScript identificados: 205
URLs interesantes filtradas: 462
Hallazgos reportables con Nuclei: 0
```

---

## Alcance y ética

Todas las actividades fueron realizadas en entornos controlados o sobre activos marcados como **in scope** dentro de un programa público de Bug Bounty.

No se realizó:

* Explotación intrusiva.
* Fuerza bruta.
* Acceso no autorizado.
* Bypass de autenticación.
* Fuzzing agresivo.
* Acciones contra sistemas fuera del alcance permitido.

---

## Herramientas utilizadas

* Kali Linux
* Windows Server 2019
* Windows 10
* Active Directory Domain Services
* Chisel
* proxychains
* NetExec
* SharpHound
* BloodHound Community Edition
* subfinder
* dnsx
* httpx
* nuclei
* katana

---

## Documentos incluidos

* `Memoria_Practica_RedTeam_Lab_Gabriel_Gutierrez.pdf`
* `Memoria_Practica_RedTeam_Recon_Gabriel_Gutierrez.pdf`

---

## Autor

**Gabriel Gutiérrez**
Práctica Red Team
Bootcamp de Ciberseguridad
