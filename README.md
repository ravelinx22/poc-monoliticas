# poc-monoliticas

PoC para curso monoliticas

Dockerfile de pulsar
-docker pull apachepulsar/pulsar:latest --platform linux/amd64

Para correrlo:
-docker run --platform linux/amd64 -it -p 6650:6650 -p 8080:8080 apachepulsar/pulsar:latest bin/pulsar standalone 

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
python3 -m flask --app src/bff  run
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
python3 -m flask --app src/productos/api run
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