# LocalTunnelConfig
Manual de configuracion LocalTunnel

# Guía para usar LocalTunnel con una API Node.js (Express)

---

## Requisitos previos

- Node.js y npm instalados en tu sistema (Ubuntu Server, Windows, etc.).
- Una aplicación Node.js (por ejemplo con Express) que escuche en un puerto (ej: 8000).
- Opcional: pm2 para mantener procesos corriendo en segundo plano.

---

## 1. Instalar Node.js y npm

Si no tienes Node.js y npm:

```
sudo apt update
sudo apt install nodejs npm -y
node -v
npm -v
```
## 2. Instalar LocalTunnel globalmente
```
npm install -g localtunnel

```
## 3. Configurar la app para que escuche en 0.0.0.0

```
this.app.listen(this.port, '0.0.0.0', () => {
  console.log(`Servidor corriendo en puerto ${this.port}`);
});
```
## 4. Ejecutar la aplicación con pm2 (opcional)

```
pm2 start app.js --name miapp
```

## 5. Ejecutar LocalTunnel para exponer la app

```
lt --port 8000 --subdomain tunelunico123
```
- Cambia 8000 por el puerto donde corre tu app.

- Cambia tunelunico123 por un subdominio único (minúsculas, sin espacios).

Esto mostrará una URL pública, por ejemplo:

```
https://tunelunico123.loca.lt
```

## 6. Desbloquear la URL si pide contraseña
Si al acceder te muestra una pantalla pidiendo contraseña, obtén la IP pública de tu servidor:

```
curl https://loca.lt/mytunnelpassword
```
## 7. Mantener LocalTunnel corriendo con pm2 (opcional)
Para que LocalTunnel se ejecute en segundo plano y arranque con el sistema:
```
pm2 start "lt --port 8000 --subdomain tunelunico123" --name localtunnel
pm2 save
pm2 startup
```

## 8. Parar LocalTunnel con pm2

```
pm2 stop localtunnel
```
