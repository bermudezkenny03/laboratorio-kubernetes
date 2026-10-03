# Laboratorio Kubernetes

Este proyecto corresponde a un laboratorio básico de Kubernetes en el que se realiza el despliegue de un servidor web Nginx utilizando Minikube, Docker Desktop y kubectl.

El objetivo principal es comprender el funcionamiento básico de Kubernetes mediante la creación de un Namespace, un Deployment con múltiples réplicas y un Service de tipo NodePort.

## Objetivo

Desplegar una aplicación web basada en Nginx dentro de un clúster local de Kubernetes utilizando Minikube como entorno de ejecución.

Durante el laboratorio se realizan las siguientes actividades:

- Creación de un Namespace.
- Creación de un Deployment.
- Despliegue de 2 réplicas de Nginx.
- Creación de un Service tipo NodePort.
- Verificación de Pods, Deployments y Services.
- Acceso a la aplicación mediante Minikube.
- Control de versiones utilizando Git.

## Tecnologías utilizadas

- Kubernetes
- Minikube
- Docker Desktop
- kubectl
- Nginx
- Git

## Estructura del proyecto

laboratorio-kubernetes/
│
├── namespace.yaml
├── deployment.yaml
├── service.yaml
└── README.md

## Descripción de los archivos

- **namespace.yaml:** crea el Namespace llamado `laboratorio`, utilizado para organizar los recursos del proyecto.
- **deployment.yaml:** crea un Deployment llamado `nginx-deployment` con 2 réplicas del servidor web Nginx.
- **service.yaml:** crea un Service llamado `nginx-service` de tipo `NodePort`, permitiendo acceder a la aplicación desplegada.
- **README.md:** contiene la documentación general del laboratorio y los principales comandos utilizados.

## Ejecución del laboratorio

Primero se crea el Namespace:

kubectl apply -f namespace.yaml

Se verifican los namespaces disponibles:

kubectl get namespaces

Se configura el Namespace `laboratorio` como predeterminado:

kubectl config set-context --current --namespace=laboratorio

Luego se crea el Deployment:

kubectl apply -f deployment.yaml

Se verifica el Deployment:

kubectl get deployments -n laboratorio

Se verifican los Pods:

kubectl get pods -n laboratorio

El Deployment está configurado con 2 réplicas, por lo que se espera encontrar dos Pods de Nginx en estado `Running`.

Después se crea el Service:

kubectl apply -f service.yaml

Se verifica el servicio:

kubectl get services -n laboratorio

El Service utilizado es de tipo `NodePort`, lo cual permite exponer la aplicación fuera del clúster local.

## Acceso a la aplicación

Para abrir la aplicación Nginx utilizando Minikube:

minikube service nginx-service -n laboratorio

También se puede obtener únicamente la URL con:

minikube service nginx-service -n laboratorio --url

## Comandos de verificación

Verificar el estado de Minikube:

minikube status

Consultar información del clúster:

kubectl cluster-info

Verificar los nodos:

kubectl get nodes

Verificar los Pods:

kubectl get pods -n laboratorio

Verificar los Deployments:

kubectl get deployments -n laboratorio

Verificar los Services:

kubectl get services -n laboratorio

## Resultado esperado

Al finalizar correctamente el laboratorio se debe tener:

- Un clúster de Minikube funcionando.
- Un Namespace llamado `laboratorio`.
- Un Deployment llamado `nginx-deployment`.
- 2 Pods de Nginx en estado `Running`.
- Un Service llamado `nginx-service`.
- Acceso al servidor web Nginx desde el navegador.

## Conclusión

Este laboratorio permite comprender de manera práctica los conceptos básicos de Kubernetes y la relación entre Namespaces, Deployments, Pods y Services.

A través de Minikube se puede trabajar con un clúster de Kubernetes de manera local, permitiendo practicar el despliegue y administración de aplicaciones antes de trabajar en entornos de producción.