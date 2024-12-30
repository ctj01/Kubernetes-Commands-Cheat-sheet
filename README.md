# Kubernetes Commands Cheat Sheet

Este repositorio contiene una recopilación de los comandos más utilizados en Kubernetes para la gestión de clústeres, pods, servicios, configuraciones y mucho más. ¡Ideal para tener a mano o como referencia rápida!

---

## Índice

1. [Configuración Inicial](#configuración-inicial)
2. [Contextos y Clústeres](#contextos-y-clústeres)
3. [Pods](#pods)
4. [Deployments](#deployments)
5. [Servicios y Exposición](#servicios-y-exposición)
6. [Namespaces](#namespaces)
7. [ConfigMaps y Secrets](#configmaps-y-secrets)
8. [Recursos y Escalado](#recursos-y-escalado)
9. [Logs y Depuración](#logs-y-depuración)
10. [Networking](#networking)
11. [Labels y Selectors](#labels-y-selectors)
12. [Seguridad y RBAC](#seguridad-y-rbac)
13. [Otros Comandos Útiles](#otros-comandos-útiles)

---

## Configuración Inicial

```bash
# Ver versión de kubectl
kubectl version --client

# Conectar kubectl a un clúster
kubectl config set-cluster [NOMBRE_CLUSTER] --server=[URL_SERVER]

# Configurar credenciales para el clúster
kubectl config set-credentials [USUARIO] --username=[USUARIO] --password=[PASSWORD]

# Crear un contexto para un clúster
kubectl config set-context [NOMBRE_CONTEXT] --cluster=[NOMBRE_CLUSTER] --namespace=[NAMESPACE]

# Usar un contexto específico
kubectl config use-context [NOMBRE_CONTEXT]
```

---

## Contextos y Clústeres

```bash
# Listar todos los contextos
kubectl config get-contexts

# Obtener información sobre el clúster actual
kubectl cluster-info

# Cambiar al contexto predeterminado
kubectl config use-context [CONTEXT_NAME]
```

---

## Pods

```bash
# Listar todos los pods en un namespace
kubectl get pods -n [NAMESPACE]

# Crear un pod desde un archivo YAML
kubectl apply -f [archivo.yaml]

# Eliminar un pod
kubectl delete pod [NOMBRE_POD]

# Ver información detallada de un pod
kubectl describe pod [NOMBRE_POD]

# Ver logs de un pod
kubectl logs [NOMBRE_POD]

# Entrar a un pod (ejecutar bash o sh dentro del contenedor)
kubectl exec -it [NOMBRE_POD] -- /bin/bash
```

---

## Deployments

```bash
# Listar deployments
kubectl get deployments

# Crear un deployment desde un archivo YAML
kubectl apply -f [archivo.yaml]

# Actualizar un deployment
kubectl set image deployment/[NOMBRE_DEPLOYMENT] [NOMBRE_CONTENEDOR]=[IMAGEN:NUEVA_VERSION]

# Escalar un deployment
kubectl scale deployment [NOMBRE_DEPLOYMENT] --replicas=[NUMERO]

# Eliminar un deployment
kubectl delete deployment [NOMBRE_DEPLOYMENT]
```

---

## Servicios y Exposición

```bash
# Listar servicios
kubectl get services

# Crear un servicio desde un archivo YAML
kubectl apply -f [archivo.yaml]

# Exponer un deployment como un servicio
kubectl expose deployment [NOMBRE_DEPLOYMENT] --type=[ClusterIP|NodePort|LoadBalancer] --port=[PUERTO]

# Eliminar un servicio
kubectl delete service [NOMBRE_SERVICIO]
```

---

## Namespaces

```bash
# Listar todos los namespaces
kubectl get namespaces

# Crear un namespace
kubectl create namespace [NOMBRE_NAMESPACE]

# Cambiar al namespace predeterminado
kubectl config set-context --current --namespace=[NOMBRE_NAMESPACE]

# Eliminar un namespace
kubectl delete namespace [NOMBRE_NAMESPACE]
```

---

## ConfigMaps y Secrets

```bash
# Crear un ConfigMap desde un archivo
kubectl create configmap [NOMBRE_CONFIGMAP] --from-file=[archivo]

# Listar ConfigMaps
kubectl get configmaps

# Crear un Secret
kubectl create secret generic [NOMBRE_SECRET] --from-literal=[clave]=[valor]

# Listar Secrets
kubectl get secrets
```

---

## Recursos y Escalado

```bash
# Ver recursos usados por los pods
kubectl top pods

# Ver recursos usados por nodos
kubectl top nodes

# Escalar un deployment
kubectl scale deployment [NOMBRE_DEPLOYMENT] --replicas=[NUMERO]
```

---

## Logs y Depuración

```bash
# Ver logs de un pod
kubectl logs [NOMBRE_POD]

# Ver logs de un pod con contenedores múltiples
kubectl logs [NOMBRE_POD] -c [NOMBRE_CONTENEDOR]

# Ver eventos del clúster
kubectl get events

# Depurar un recurso
kubectl describe [recurso] [NOMBRE_RECURSO]
```

---

## Networking

```bash
# Ver todos los ingress
kubectl get ingress

# Crear un ingress desde un archivo YAML
kubectl apply -f [archivo.yaml]

# Eliminar un ingress
kubectl delete ingress [NOMBRE_INGRESS]

# Probar conectividad dentro del clúster
kubectl run -it --rm debug --image=busybox -- /bin/sh
```

---

## Labels y Selectors

```bash
# Agregar un label a un recurso
kubectl label [tipo_recurso]/[nombre_recurso] [clave]=[valor]

# Eliminar un label de un recurso
kubectl label [tipo_recurso]/[nombre_recurso] [clave]-

# Listar recursos con un label específico
kubectl get [tipo_recurso] -l [clave]=[valor]

# Ver detalles de labels en un recurso
kubectl describe [tipo_recurso] [nombre_recurso]

# Usar un selector para filtrar recursos
kubectl get [tipo_recurso] --selector [clave]=[valor]
```

---

## Seguridad y RBAC

```bash
# Crear un ServiceAccount
kubectl create serviceaccount [NOMBRE_CUENTA]

# Listar ServiceAccounts
kubectl get serviceaccounts

# Asociar un Role a un ServiceAccount
kubectl create rolebinding [NOMBRE_ROLEBINDING] --role=[NOMBRE_ROLE] --serviceaccount=[NAMESPACE]:[NOMBRE_CUENTA]

# Asociar un ClusterRole a un ServiceAccount
kubectl create clusterrolebinding [NOMBRE_CLUSTERROLEBINDING] --clusterrole=[NOMBRE_CLUSTERROLE] --serviceaccount=[NAMESPACE]:[NOMBRE_CUENTA]

# Ver roles en el clúster
kubectl get roles

# Ver roles a nivel de clúster
kubectl get clusterroles

# Ver bindings de roles
kubectl get rolebindings

# Ver bindings de cluster roles
kubectl get clusterrolebindings

# Eliminar un RoleBinding o ClusterRoleBinding
kubectl delete [rolebinding|clusterrolebinding] [NOMBRE_BINDING]
```

---

## Otros Comandos Úitiles

```bash
# Aplicar cambios desde un archivo YAML
kubectl apply -f [archivo.yaml]

# Eliminar un recurso desde un archivo YAML
kubectl delete -f [archivo.yaml]

# Ejecutar un comando en un pod
kubectl exec [NOMBRE_POD] -- [COMANDO]

# Obtener información sobre el estado de los nodos
kubectl get nodes
```

---

## Contribuciones

¡Las contribuciones son bienvenidas! Si tienes algún comando que crees que debería estar aquí, por favor crea un pull request.

---

© 2024. Creado por [@ctj01].

