# 📊 Zabbix - Docker Ambiente Local

Despliegue completo de Zabbix usando Docker Compose, ideal para laboratorio, pruebas y demostración profesional.

---

## 📝 Descripción

Este proyecto permite desplegar Zabbix de forma rápida y reproducible en un entorno local utilizando Docker Compose.

Está pensado para:

- Monitoreo de servidores
- Laboratorio DevOps
- Pruebas de alertas
- Aprendizaje Zabbix

---

## 📦 Componentes

- Zabbix Server
- Zabbix Web (Nginx)
- MySQL 8

---

## 📂 Estructura del Proyecto

```
ZABBIX-DOCKER-AMBIENTE-LOCAL/
├── docker-compose.yml
├── .env.example
├── .gitignore
├── README.md
├── docs/
│   ├── arquitectura.md
│   └── screenshots.md
├── scripts/
│   ├── init-db.sh
│   └── backup.sh
└── data/
    ├── mysql/
    └── zabbix/
```

---

## 🚀 Uso

```bash
# Crear estructura de carpetas
mkdir ZABBIX-DOCKER-AMBIENTE-LOCAL
cd ZABBIX-DOCKER-AMBIENTE-LOCAL
mkdir docs scripts data
mkdir data/mysql data/zabbix

# Iniciar servicios
docker compose up -d
```

**Acceso web:** http://localhost:8080

**Credenciales por defecto:**
- Usuario: Admin
- Password: zabbix

---

## 🛠️ Comandos Útiles

```bash
docker compose ps
docker compose logs -f zabbix-server
docker compose down
```

---

## 🔐 Seguridad

- Cambiar contraseñas por defecto
- No exponer puertos en producción
- Usar proxy reverso con SSL

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
