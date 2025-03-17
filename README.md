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

## Paso 2: Instalación de Chrony
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

---

## Paso 3: Instalación de stack LAMP
1. Instalar **LAMP**
    *LAMP sirve para que el servidor ubuntu se convierta en una plataforma para alojar aplicaciones web dinámicas*
     - **L --> LINUX**  
     - **A --> APACHE**  
     - **M --> MYSQL**  
     - **P --> PHP**  

### Comandos para instalar y configurar LAMP
```bash
sudo apt install mariadb-server php php-cli php-common php-fpm php-curl php-mysql apache2 curl
```
1. Configuración de MariaDB
```bash
sudo systemctl enable mariadb
```

```bash
sudo systemctl status mariadb
```
```bash
sudo systemctl status mariadb
```
```bash
sudo mysql_secure_installation
```
2. Crear base de datos para Zabbix
```bash
sudo mysql -u root -p
password
mysql> create database zabbix character set utf8mb4 collate utf8mb4_bin;
mysql> create user zabbix@localhost identified by 'password';
mysql> grant all privileges on zabbix.* to zabbix@localhost;
mysql> set global log_bin_trust_function_creators = 1;
mysql> quit;
```

3. Configurar el servicio de Apache

```bash
sudo systemctl enable apache2
```
```bash
sudo systemctl status apache2
```
- **Verificamos localización configurada en Ubuntu Server**
```bash
locale -a
```

```bash
sudo locale-gen en_US.UTF-8
```

```bash
sudo update-locale
```
- **Modificamos configuración de php**


```bash
sudo nano /etc/php/8.3/cli/php.ini
```


Cambiamos las siguientes variables
memory_limit = 2G
max_execution_time = 360
date.timezone = America/Mexico-City (Le quitamos el comentario)
cgi.fix.pathinfo = 0 (Le quitamos el comentario)

---