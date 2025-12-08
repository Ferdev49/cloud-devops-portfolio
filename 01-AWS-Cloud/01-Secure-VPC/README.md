# 🛡️ Proyecto 1: Arquitectura VPC Segura desde Cero

## 🎯 Objetivo
Implementar una Virtual Private Cloud (VPC) en AWS con enfoque en **seguridad desde el diseño**, aplicando principios de mínimo privilegio y segmentación de red para proteger recursos en la nube.

## 📅 Información del Proyecto
- **Fecha:** 8 de diciembre 2025
- **Región AWS:** us-east-2 (Ohio)
- **Tiempo de ejecución:** 45 minutos
- **Costo total:** $0.00 (todos los recursos en Free Tier)
- **Estado:** ✅ Completado

## 🏗️ Arquitectura Implementada

### Diagrama de Red
![Arquitectura VPC Segura]
![VPC](./[screenshots/vpc-created.png](https://github.com/Ferdev49/cloud-devops-portfolio/blob/main/01-AWS-Cloud/01-Secure-VPC/Captura%20de%20pantalla%202025-12-08%20130901.png))
![Subnets](./screenshots/subnets-configured.png)
![IGW](./screenshots/igw-attached.png)
![Route Table](./screenshots/route-table.png)
![Security Groups](./screenshots/security-groups.png)
![Flow Logs](./screenshots/flow-logs.png)

### Componentes de Infraestructura
```yaml
VPC Principal:
  Nombre: vpc-secure-ferdev49
  CIDR Block: 10.0.0.0/16
  DNS Support: Enabled
  DNS Hostnames: Enabled

Subredes (Segmentación por función):
  - public-subnet-1:
      CIDR: 10.0.1.0/24
      AZ: us-east-2a
      Propósito: Recursos con IP pública
      Route Table: Asociada a Internet
  
  - private-app-subnet-1:
      CIDR: 10.0.2.0/24
      AZ: us-east-2a
      Propósito: Servidores de aplicación
      Acceso: Solo desde subred pública
  
  - private-db-subnet-1:
      CIDR: 10.0.3.0/24
      AZ: us-east-2b
      Propósito: Bases de datos aisladas
      Acceso: Solo desde subred de aplicación

Conectividad:
  Internet Gateway: igw-secure-ferdev49
  Route Table: rt-public-ferdev49
  Ruta configurada: 0.0.0.0/0 → Internet Gateway
