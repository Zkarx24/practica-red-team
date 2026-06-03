# Práctica Red Team - Gabriel Gutiérrez

Este repositorio contiene la entrega de la **Práctica Red Team**, separada en dos memorias técnicas:

1. **Memoria_Practica_RedTeam_Lab_Gabriel_Gutierrez.pdf**
2. **Memoria_Practica_RedTeam_Recon_Gabriel_Gutierrez.pdf**

---

## 1. Red Team Lab

La memoria **Red Team Lab** documenta la construcción de un laboratorio interno basado en **Active Directory**, segmentación de red, pivoting y análisis de relaciones de privilegios.

### Contenido principal

- Preparación de un dominio Windows `lab.local`.
- Configuración de Windows Server 2019 como controlador de dominio `CD01`.
- Configuración de Windows 10 como estación de trabajo y máquina pivot.
- Validación de segmentación entre Kali, Windows 10 y CD01.
- Uso de **Chisel** para crear un túnel reverse SOCKS.
- Uso de **proxychains** para redirigir tráfico desde Kali hacia la red interna.
- Validación de acceso SMB y LDAP mediante **NetExec**.
- Recolección de información del dominio con **SharpHound**.
- Análisis de relaciones de privilegios con **BloodHound**.
- Identificación de una ruta de privilegios desde `GABO@LAB.LOCAL` hacia `BACKUP OPERATORS@LAB.LOCAL`.

### Hallazgo principal

Se identificó una delegación insegura de privilegios:

```text
GABO@LAB.LOCAL
  -> IT_BACKUP_OPERATORS@LAB.LOCAL
  -> BACKUP OPERATORS@LAB.LOCAL
