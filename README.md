📦 Proyecto: ZABBIX-DOCKER-AMBIENTE-LOCAL

Despliegue completo de Zabbix usando Docker Compose, ideal para laboratorio, pruebas y demostración profesional.

🧱 Arquitectura
ZABBIX-DOCKER-AMBIENTE-LOCAL
│
├── docker-compose.yml
├── .env.example
├── .gitignore
├── README.md
│
├── docs/
│   ├── arquitectura.md
│   └── screenshots.md
│
├── scripts/
│   ├── init-db.sh
│   └── backup.sh
│
└── data/
    ├── mysql/
    └── zabbix/

📂 1️⃣ Estructura de Carpetas (crear tal cual)
mkdir ZABBIX-DOCKER-AMBIENTE-LOCAL
cd ZABBIX-DOCKER-AMBIENTE-LOCAL

mkdir docs scripts data
mkdir data/mysql data/zabbix

🐳 2️⃣ docker-compose.yml
version: "3.8"

services:

  mysql:
    image: mysql:8.0
    container_name: zabbix-mysql
    restart: always
    environment:
      MYSQL_DATABASE: zabbix
      MYSQL_USER: zabbix
      MYSQL_PASSWORD: zabbix_pass
      MYSQL_ROOT_PASSWORD: root_pass
    volumes:
      - ./data/mysql:/var/lib/mysql

  zabbix-server:
    image: zabbix/zabbix-server-mysql:latest
    container_name: zabbix-server
    restart: always
    depends_on:
      - mysql
    environment:
      DB_SERVER_HOST: mysql
      MYSQL_DATABASE: zabbix
      MYSQL_USER: zabbix
      MYSQL_PASSWORD: zabbix_pass
    ports:
      - "10051:10051"
    volumes:
      - ./data/zabbix:/var/lib/zabbix

  zabbix-web:
    image: zabbix/zabbix-web-nginx-mysql:latest
    container_name: zabbix-web
    restart: always
    depends_on:
      - mysql
      - zabbix-server
    environment:
      DB_SERVER_HOST: mysql
      MYSQL_DATABASE: zabbix
      MYSQL_USER: zabbix
      MYSQL_PASSWORD: zabbix_pass
      ZBX_SERVER_HOST: zabbix-server
      PHP_TZ: America/Guayaquil
    ports:
      - "8080:8080"

🔐 3️⃣ .env.example
MYSQL_DATABASE=zabbix
MYSQL_USER=zabbix
MYSQL_PASSWORD=zabbix_pass
MYSQL_ROOT_PASSWORD=root_pass
TZ=America/Guayaquil


👉 En GitHub subes .env.example, no .env

🚫 4️⃣ .gitignore
.env
data/
*.log

📘 5️⃣ README.md (profesional para tu perfil)
# 🖥️ Zabbix en Docker – Ambiente Local

Despliegue completo de Zabbix usando Docker Compose, ideal para monitoreo, laboratorio y demostraciones técnicas.

## 📦 Componentes
- Zabbix Server
- Zabbix Web (Nginx)
- MySQL 8

## 📂 Estructura


ZABBIX-DOCKER-AMBIENTE-LOCAL
├── docker-compose.yml
├── .env.example
├── README.md
└── data/


## ▶️ Uso

```bash
docker compose up -d


Acceso web:

http://localhost:8080


Credenciales por defecto:

Usuario: Admin

Password: zabbix

🛠️ Comandos útiles
docker compose ps
docker compose logs -f zabbix-server
docker compose down

📊 Casos de uso

Monitoreo de servidores

Laboratorio DevOps

Pruebas de alertas

Aprendizaje Zabbix

🔐 Seguridad

Cambiar contraseñas por defecto

No exponer puertos en producción

Usar proxy reverso con SSL

✍️ Autor

Isaac Haro

---

## 👨‍💻 Desarrollado por Isaac Esteban Haro Torres

**Ingeniero en Sistemas · Full Stack · Automatización · Data**

- 📧 Email: zackharo1@gmail.com
- 📱 WhatsApp: 098805517
- 💻 GitHub: https://github.com/ieharo1
- 🌐 Portafolio: https://ieharo1.github.io/portafolio-isaac.haro/

---

## 📄 Licencia

© 2026 Isaac Esteban Haro Torres - Todos los derechos reservados.

git branch -M main
git remote add origin https://github.com/TU_USUARIO/ZABBIX-DOCKER-AMBIENTE-LOCAL.git
git push -u origin main
