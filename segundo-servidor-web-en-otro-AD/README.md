# Segundo Servidor Web en OCI con Terraform

En esta lección, agregaremos una segunda VM en otro Dominio de Disponibilidad (AD) dentro de la misma Virtual Cloud Network (VCN) y subred regional. Dentro de esta nueva VM, nuevamente utilizaremos el Null Provider para configurar otro servidor web con contenido sencillo en la página principal. Sin embargo, esta vez mostrará el siguiente contenido: "¡Bienvenido a Example.com! Este es WEBSERVER2..."

## Objetivo

Después de esta sección, podrás usar las direcciones IP públicas de ambas VMs para acceder a dos páginas web diferentes. ¿No sería genial tener un balanceador de carga sobre estas VMs y ocultar ambos servidores web bajo la sombrilla del balanceador de carga?

## Estructura del Repositorio

- **Compartment**: Un compartimento para aislar los recursos.
- **VCN (Virtual Cloud Network)**: Una red virtual con una subred pública regional que cubre todos los dominios de disponibilidad (AD1-AD3).
- **Subred Pública**: Regional, cubriendo todos los AD.
- **Dos VMs para WebServers**:
  - **WebServer1**: En el primer dominio de disponibilidad.
  - **WebServer2**: En un segundo dominio de disponibilidad.
- **Internet Gateway y Tabla de Rutas**: Para permitir el tráfico de entrada y salida.
- **Lista de Seguridad Básica**: Permite acceso SSH, HTTP y HTTPS.
- **Provisionamiento con Terraform**: Utiliza `null_resource` y `remote-exec` para instalar el servidor HTTP y desplegar contenido web en ambas VMs.

## Contenido Web

- **WEBSERVER1**: "¡Bienvenido a Example.com! Este es WEBSERVER1."
- **WEBSERVER2**: "¡Bienvenido a Example.com! Este es WEBSERVER2."

## Próximos Pasos

Considera la posibilidad de agregar un balanceador de carga para distribuir el tráfico entre los dos servidores web, mejorando la disponibilidad y la escalabilidad de tu infraestructura.