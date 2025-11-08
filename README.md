## Instalación de Jenkins in Docker


### Paso 1: Descargar la imagen oficial de Jenkins
```
docker pull jenkins/jenkins:lts-jdk17
```

### Paso 2: Crear un contenedor de Jenkins
```
docker run -d  -p 8080:8080  -p 50000:50000  -v jenkins_home:/var/jenkins_home  --name jenkins  jenkins/jenkins:jdk17
```

### Paso 3: Acceder a Jenkins
Ingresa a  http://localhost:8080/

### Paso 4: Obtener la contraseña inicial
```
docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```
### Paso 5: Completar la configuración inicial      
- Ingresa la contraseña obtenida en el paso anterior.
- Selecciona "Instalar los complementos recomendados".
- Crea el primer usuario administrador.

### Paso 6: Installar maven en el Contenedor de Jenkins 
```
docker exec -u root -it jenkins bash
apt update
apt install maven -y
```
### Paso 7: Donde estan instalados Java, Maven y git en el contenedor de Jenkins
```
dirname $(dirname $(readlink -f $(which java)))
dirname $(dirname $(readlink -f $(which mvn)))
which git

```
    

