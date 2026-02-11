# 🐳FastAPI-K8s-App-Sistema-Distribuido-con-Minikube
<img width="1024" height="1024" alt="image" src="https://github.com/user-attachments/assets/879eb896-5483-4630-8107-ee8ef797caa6" />
Este proyecto desarrolla una arquitectura de microservicios distribuida basada en FastAPI como framework principal, utilizando Redis para mensajería y caché, PostgreSQL como sistema de persistencia de datos y Nginx como proxy inverso y balanceador de carga. La solución se encuentra contenedorizada y orquestada en un clúster de Kubernetes (Minikube), garantizando escalabilidad, aislamiento de servicios y una gestión eficiente del tráfico y los recursos.

# 📦Componentes del sistema
| Componente        | Función                                                     |
|-------------------|-------------------------------------------------------------|
| **FastAPI + Uvicorn** | API stateless con endpoints `/` y `/db`                     |
| **Redis**         | Almacenamiento en caché y contador de visitas               |
| **PostgreSQL**    | Base de datos para persistencia                             |
| **Nginx**         | Balanceador de carga para múltiples réplicas                |

# 📁Estructura del proyecto
```text
fastapi_k8s_app/
├── app/
│   └── main.py              # Código de la API FastAPI
├── k8s/
│   ├── app.yaml             # Despliegue y servicio para FastAPI
│   ├── redis.yaml           # Redis deployment + service
│   ├── postgres.yaml        # PostgreSQL deployment + PV + service
│   └── nginx.yaml           # Configuración balanceador Nginx
├── Dockerfile               # Imagen personalizada para FastAPI
├── build_and_reload.sh      # Script de despliegue sin Docker Desktop
└── README.md                # Este archivo
```
# 🚀Cómo desplegar
# Requisitos:
- [ ] Docker Desktop (opcional)
- [x] Minikube
- [x] kubectl

# 1. Inicia Minikube
```
minikube start
```
# 2. Construye la imagen dentro de Minikube
```
minikube image build -t fastapi-app:latest .
```
> 💡 **Si usas Docker Desktop y no estás en entorno Minikube, puedes usar `docker build` + `minikube image load`.**



