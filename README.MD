# Jenkins-SonarQube-Docker
Despliegue de una aplicacion web en un entorno contenerizado con Docker, a su vez pipeline de CI-CD con trigger en GItHub con Actions y revisiòn de codigo con SonarQube para estandares de calidad. 

**

## Procedimiento de creaciòn de instancia EC2 para servicios, Jenkins, Docker y SonarQube.

**
-Creaciòn tres instancias(Jenkins,SonarQube,Docker), 4gb ram 2 cpus. Ubuntu.
-Jenkins: Instalacion de Jenkins en su correspondiente instancia EC2.
-Jenkins: update del sistema, instalacion del openjdk 11, e instalaciòn de Jenkins.

sudo apt install openjdk-11-jre-headless

sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins

- Verificar que Jenkins estè corriendo con normalidad:
systemctl status jenkins

-Configurar Jenkins, poner contraseña, instalar suggested plugins.
-Cargar en un repositorio publico en Git nuestro proyecto web, y luego
asociar a traves de webhooks el repositorio a Jenkins para que cuando 
se ejecuten cambios en el repo, automaticamente se dispare el pipeline.
