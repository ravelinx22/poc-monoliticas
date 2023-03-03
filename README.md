# PoC monoliticas

PoC para curso monoliticas

## Integrantes

- Andres Baron
- Emilson Quintero
- Laura Bello
- William Ravelo

## Arquitectura

En el siguiente diagrama se puede ver los componentes y topicos principales al igual que su interacción.

![Base monoliticas drawio (1)](https://user-images.githubusercontent.com/16025512/222797394-c0005067-1ea4-4c8e-8f3d-bddefd65a9f3.png)

De igual forma el siguiente diagrama presenta a nivel de componentes como fueron desplegados

![Base monoliticas drawio (2)](https://user-images.githubusercontent.com/16025512/222797509-9463e90c-7b79-4334-8a1f-b96f05d5a8dd.png)

## DDD

En este diagrama se pueden ver los contextos acotados implementados junto con sus dominios

![Base monoliticas drawio](https://user-images.githubusercontent.com/16025512/222797116-9794b27a-7f93-4699-9163-bfe2f449a1ed.png)

## Escenarios de calidad a probar

## Justificaciones

##### Se justifica correctamente los tipos de eventos a utilizar (integración o carga de estado). Ello incluye la definición de los esquemas y evolución de los mismos.

Justificacion

##### Justificó e implementó alguna de las topologías para la administración de dato

Justificacion

## Descripción de actividades

- Andres Baron
- Emilson Quintero
- Laura Bello
- William Ravelo
- Todos

## Requisitos

- Python 3
- Apache pulsar

## Pulsar desde dockerfile

Dockerfile de pulsar

```bash
docker pull apachepulsar/pulsar:latest --platform linux/amd64
```

Para correrlo:

```bash
docker run --platform linux/amd64 -it -p 6650:6650 -p 8080:8080 apachepulsar/pulsar:latest bin/pulsar standalone 
```

### Tmux

Para desplegar y tener multiples sesiones se uso tmux, estos son algunos comandos frecuentes

- Crear nueva sesion con nombre

```bash
tmux new -s <NAME>
```

- Conectarse a sesion

```bash
tmux attach-session -t <NAME>
```

- Desconectarse de sesion

```bash
tmux detach -s <NAME>
```

- Listar sesiones

```bash
tmux ls
```

- Renombrar ventana

```bash
tmux rename-window '<NAME>'
```

### Variables de entorno

Se necesitan las siguientes variables de entorno

```bash
export DB_USERNAME=
export DB_PASSWORD=
export DB_HOSTNAME=
export DB_NAME=
export BROKER_HOST=
export DB_READ_NAME=
export DB_READ_HOSTNAME=
```

### Crear ambiente con conda

```bash
conda create --name monoliticas
```

### Usar ambiente con conda

```bash
conda activate monoliticas
```

### Instalar dependencias

```bash
pip install -r requirements.txt
pip install -r conductores-requirements.txt
```

## Microservicio BFF

Desde el directorio principal ejecute el siguiente comando.

```bash
flask --app src/bff  run
python3 -m flask --app src/bff  run --host=0.0.0.0 -p 3000
```

## Microservicio ordenes

Desde el directorio principal ejecute el siguiente comando.

```bash
python3 src/ordenes/consumer.py
```

## Microservicio productos

Desde el directorio principal ejecute el siguiente comando.

```bash
flask --app src/productos/api run
python3 -m flask --app src/productos/api run --host=0.0.0.0 -p 3001
```

## Microservicio conductores

Desde el directorio principal ejecute el siguiente comando.

```bash
python3 src/conductores/consumer.py
```

## Utils
### Correr pulsar

```bash
export DOCKER_DEFAULT_PLATFORM=linux/amd64
docker-compose --profile pulsar up
```

### Correr db

```bash
export DOCKER_DEFAULT_PLATFORM=linux/amd64
docker-compose --profile db up
```

### Parar pulsar

```bash
docker-compose --profile pulsar stop
```

### Parar db

```bash
docker-compose --profile db stop
```

### Consumer tester

```bash
python ./testers/consumer_tester.py
```

### Producer tester

```bash
python ./testers/producer_tester.py
```
