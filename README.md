# Pasos para la instalación de un servidor en Zabbix

## Paso 1: Instalación de Ubuntu Server
1. Descargar Ubuntu Server desde la página oficial: [https://ubuntu.com/download/server](https://ubuntu.com/download/server)  
2. Utilizar una máquina virtual para emular el servidor. En este caso, se usó **Oracle VM VirtualBox**: [https://www.virtualbox.org](https://www.virtualbox.org)  
   - Configurar los parámetros que utilizará el servidor:
     - **RAM**  
     - **Almacenamiento**  
     - **Procesador**  
     - **Otros recursos**  

---

## Paso 2: Instalación de Zabbix
1. Instalar **Chrony**  
   *Chrony es una implementación flexible de NTP (Protocolo de Tiempo de Red) que permite sincronizar el reloj del sistema desde diferentes servidores NTP, relojes de referencia o mediante una entrada manual.*

### Comandos para instalar y configurar Chrony:
```bash
sudo apt install chrony
```
```bash
sudo systemctl enable chrony
```
```bash
sudo systemctl status chrony
```
```bash
sudo systemctl set-timezone America/Mexico-City
```