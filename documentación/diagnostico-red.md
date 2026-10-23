# Diagnóstico de conectividad de red

## 1. Objetivo

Comprobar la conectividad de red del servidor `SRV-AD01`, la resolución de nombres DNS y la posibilidad de establecer una conexión TCP con un servicio HTTPS externo.

## 2. Entorno de laboratorio

- **Servidor:** SRV-AD01
- **Sistema operativo:** Windows Server 2025 Standard Evaluation
- **Hipervisor:** Oracle VirtualBox
- **Modo de red:** NAT
- **Dirección IPv4 del servidor:** 10.0.2.15
- **Puerta de enlace:** 10.0.2.2

## 3. Pruebas realizadas

### 3.1. Comprobar la conectividad con la puerta de enlace

**Comando:**

`ping 10.0.2.2`

**Resultado:** 4 paquetes recibidos y 0 % de pérdida.

**Interpretación:** el servidor responde a las solicitudes ICMP dirigidas a la puerta de enlace virtual.

### 3.2. Comprobar la resolución DNS

**Comando:**

`nslookup www.microsoft.com`

**Resultado:** la consulta devolvió direcciones IP asociadas al nombre solicitado.

**Interpretación:** la resolución DNS funcionó correctamente en el momento de la prueba. El mensaje `Servidor: UnKnown` no impidió completar la consulta.

### 3.3. Comprobar la conectividad TCP con HTTPS

**Comando:**

`Test-NetConnection www.microsoft.com -Port 443`

**Resultado:** `TcpTestSucceeded: True`.

**Interpretación:** se estableció una conexión TCP con el destino en el puerto 443.

## 4. Conclusión

Las tres pruebas finalizaron correctamente. Se comprobó la conectividad con la puerta de enlace, la resolución DNS y el establecimiento de una conexión TCP con un servicio externo.

Estas pruebas no verifican todavía la conectividad con recursos compartidos SMB ni el funcionamiento de Active Directory.

## 5. Próximos pasos

- Preparar la configuración de DNS para el futuro dominio de laboratorio.
- Instalar y configurar Active Directory Domain Services (AD DS).
- Realizar nuevas pruebas de conectividad a medida que se incorporen servicios al laboratorio.

## 6. Evidencias

### Conectividad con la puerta de enlace y resolución DNS

![Resultados de ping a la puerta de enlace y consulta DNS](../capturas/ping-puerta-enlace-y-dns.png)

### Comprobación de conectividad y puertos

![Resultado de las pruebas de conectividad y puerto HTTPS](../capturas/ping-conexion-puertos.png)

