# Practica-2do-Parcial-Ansible-lab
 
## Objetivo

Crear un laboratorio con dos servidores Linux usando Docker y administrarlos con Ansible, aplicando conceptos básicos de automatización: inventario, módulos, loops y condicionales.

## Estructura del proyecto

```text
ansible-lab/
├── docker-compose.yml
├── inventory.ini
├── playbook.yml
└── README.md
```

## Requisitos

- Docker y Docker Compose instalados
- Ansible instalado
- Python3 (se instala dentro de los contenedores)

## Iniciar los contenedores

```bash
docker compose up -d
docker ps
```

## Instalar Python en cada contenedor

```bash
docker exec -it server1 bash -c "apt update && apt install -y python3"
docker exec -it server2 bash -c "apt update && apt install -y python3"
```

## Verificar la conexión con Ansible

```bash
ansible docker -i inventory.ini -m ping
```

## Ejecutar el playbook

```bash
ansible-playbook -i inventory.ini playbook.yml
```

El playbook realiza lo siguiente en ambos servidores:

- Muestra el hostname.
- Muestra el sistema operativo.
- Crea el directorio `/tmp/ansible-demo`.
- Crea el archivo `info.txt` con el nombre del servidor y su sistema operativo.
- Crea, mediante un loop, los directorios `logs`, `backup` y `config`.
- Muestra un mensaje solo cuando el sistema operativo es Ubuntu.

## Captura de pantalla

<img width="1914" height="957" alt="image" src="https://github.com/user-attachments/assets/3ae25394-e8a2-4105-9361-f9d71a5dd48c" />

