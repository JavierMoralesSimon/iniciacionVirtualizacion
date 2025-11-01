# Descripción del proceso de instalación de Ubuntu en VirtualBox
1. Descarga de un archivo .iso desde la página oficial de Ubuntu, en nuestro caso el de la versión 24.04 LTS.
2. Creación de la máquina que usa dicha .iso en VirtualBox, poniendo la configuración deseada. En nuestro caso es:
    * Nombre: Ubuntu-DAW2DAW
    * RAM: 4096 MB
    * Disco duro virtual: mínimo 50 GB
    * Tipo de red: NAT
3. Encender la máquina virtual y seguir el proceso de instalación.
4. Instalar las Guest Additions.

Captura de pantalla del escritorio una vez terminado el proceso:
![Escritorio de Ubuntu 24.04 LTS](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/1.png)

# Pasos seguidos para instalar Docker Desktop
1. Actualizar los repositorios:
    * Comando: `sudo apt update && sudo apt upgrade -y`
    * Captura de pantalla: ![Actualizar los repositorios](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/2.png)
2. Instalar dependencias:
    * Comando: `sudo apt install ca-certificates curl gnupg -y`
    * Captura de pantalla: ![Instalar dependencias](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/3.png)
3. Añadir el repositorio oficial de Docker:

   **3.1.** Primero, descargar y añadir la clave GPG de Docker:
   
        - Comando: `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`  
   **3.2.** Segundo, añadir el repositorio de Docker a las fuentes de APT para la versión correcta de Ubuntu:
   
        - Comando: `echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null`
   
**Captura de pantalla:** ![Añadir el repositorio oficial de Docker](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/4.png)
5. Actualizar el índice de paquetes para que el sistema reconozca el nuevo repositorio de Docker:
    * Comando: `sudo apt update`
    * Captura de pantalla: ![Actualizar el índice de paquetes para que el sistema reconozca el nuevo repositorio de Docker](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/5.png)
6. Instalar Docker Engine, que es necesario para Docker Desktop:
    * Comando: `sudo apt install docker-ce docker-ce-cli containerd.io -y`
    * Captura de pantalla: ![Instalar Docker Engine](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/6.png)
7. Descargar e instalar el paquete .deb de Docker Desktop:
   **6.1.** Primero asegurarse de tener "Snap" instalado y si no, hacerlo. Es la forma recomendada para instalar Docker Desktop en distribuciones Linux modernas:
        - Comando: `sudo apt install snapd -y`  
        - Captura de pantalla: ![Ver si Snap está instalado](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/7.png)
   **6.2.** Segundo, instalar Docker Desktop usando Snap:
        - Comando: `sudo snap install docker --classic`
        - Captura de pantalla: ![Instalar Docker Desktop usando Snap](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/8.png)
8. Verificar que funciona correctamente:
    **7.1.** Comprobación de la instalación:
        - Comando: `docker --version`  
        - Captura de pantalla: ![Verificar funcionamiento](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/9.png)
   **7.2.** Prueba de uso:
        - Comando: `sudo docker run hello-world`
        - Captura de pantalla: ![Prueba de uso](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/10.png)

# Comandos usados para crear y ejecutar los contenedores
1. Buscar imágenes disponibles:
   **1.1.** Nginx:
        - Comando: `sudo docker search nginx`  
        - Captura de pantalla: ![Buscar imagen de Nginx](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/11.png)
   **1.2.** Tomcat:
        - Comando: `sudo docker search tomcat`
        - Captura de pantalla: ![Buscar imagen de Tomcat](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/12.png)
2. Descargar e iniciar contenedores:
   **2.1.** Nginx:
        - Comando: `sudo docker run -d -p 8080:80 --name webserver nginx`  
        - Captura de pantalla: ![Descargar e iniciar Nginx](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/13.png)
   **2.2.** Tomcat:
        - Comando: `sudo docker run -d -p 8081:8080 --name appserver tomcat`
        - Captura de pantalla: ![Descargar e iniciar Tomcat](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/14.png)
3. Verificar contenedores activos:
    * Comando: `sudo docker ps`
    * Captura de pantalla: ![Verificar contenedores activos](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/15.png)
4. Abrir en el navegador:
   **4.1.** Nginx:
        - Url: `http://localhost:8080`  
        - Captura de pantalla: ![Abrir Nginx en el navegador](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/16.png)
   **4.2.** Tomcat:
        - Url: `http://localhost:8081`
        - Captura de pantalla: ![Abrir Tomcat en el navegador](https://github.com/JavierMoralesSimon/iniciacionVirtualizacion/blob/main/Capturas/17.png)

# Descripción de los requerimientos mínimos para implantar una aplicación web:
* ### Requisitos de hardware y software:
    * Hardware:
        * Procesador de al menos 2 núcleos, 4 GB de RAM y 20 GB de almacenamiento libre. En función del tráfico esperado, igual más.
        * Un equipo con navegador actualizado y conexión estable a Internet.
        * Almacenamiento adicional o externo para backups automáticos.
    * Software:
        * Un sistema operativo para el servidor como por ejemplo Linux o Windows Server.
        * Un servidor web como por ejemplo Nginx.
        * Un servidor de aplicaciones como por ejemplo Tomcat.
        * Una base de datos como por ejemplo MySQL.
        * Lenguajes y frameworks como por ejemplo Python y Django.
        * Navegadores compatibles como por ejemplo Chrome.
* ### Infraestructura de red: 
    * Ancho de banda suficiente para soportar el tráfico estimado.
    * Dirección IP fija (pública) o uso de DNS dinámico si el servidor se aloja internamente.
    * Cortafuegos configurado para permitir solo los puertos necesarios.
    * Balanceador de carga si se esperan muchos usuarios simultáneos.
    * Certificado SSL/TLS para comunicación cifrada.
    * Acceso remoto seguro mediante SSH o VPN para tareas administrativas.
* ### Configuración del servidor web y de aplicaciones:
    * Instalación y configuración del servidor web para servir los archivos estáticos y redirigir peticiones al backend.
    * Configuración del servidor de aplicaciones para gestionar la lógica de negocio.
    * Definición de variables de entorno.
    * Configuración de logs de acceso y errores para el monitoreo.
    * Pruebas de despliegue antes de la publicación.
    * Automatización del despliegue.
* ### Seguridad y mantenimiento:
    * Actualizaciones periódicas del sistema operativo, librerías y frameworks.
    * Control de acceso mediante autenticación y autorización.
    * Uso de HTTPS para cifrar la comunicación.
    * Copias de seguridad automáticas y verificación de restauración.
    * Monitorización continua.
    * Políticas de contraseñas seguras y cifrado de datos sensibles.
    * Pruebas de vulnerabilidad y auditorías de seguridad.

    * Planes de contingencia ante fallos o ataques.
