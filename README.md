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

