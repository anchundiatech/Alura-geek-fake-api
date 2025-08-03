# Alura Geek Fake API

API REST simulada para el proyecto Alura Geek, ideal para pruebas y prototipos de e-commerce. Implementada con [JSON Server](https://github.com/typicode/json-server) y desplegada en [Render](https://render.com).

![Render](https://img.shields.io/badge/Deploy-Render-0078d7?logo=render)

## 🚀 Demo

(Coloca aquí la URL pública de tu API desplegada en Render, ejemplo: https://alurageek-api.onrender.com)

## ✨ Características

- API REST lista para usar, sin backend real  
- Endpoints para productos y categorías  
- CRUD completo (Crear, Leer, Actualizar, Eliminar)  
- Despliegue automático en Render  

## ⚡ Inicio Rápido

1. Clona este repositorio o crea uno nuevo usando este código.  
2. Actualiza el archivo [`db.json`](./db.json) con tus datos.  
3. Crea una cuenta o inicia sesión en [Render](https://render.com).  
4. Crea un nuevo servicio Web Service en Render y conecta tu repositorio.  
5. En el comando de inicio, usa:  
node server.js

bash
Copiar
Editar
6. Define la variable de entorno `PORT` o usa el puerto por defecto `3000` en tu `server.js`.  
7. Despliega y espera que Render levante tu servicio 🎉.  

## 📦 Estructura de `db.json`

```json
{
"product": [
 {
   "img": "https://www.claroshop.com/c/star-wars-day/img/categorias/TAZAS_CATEGORIAS_STAR_WARS.png",
   "name": "Taza Trooper",
   "price": "$60.00",
   "description": "Taza con diseño de casco Trooper",
   "category": "starwars",
   "id": 1
 },
 {
   "img": "https://cdn1.coppel.com/images/catalog/mkp/1773/5000/17733590-1.jpg",
   "name": "Funko Darth Vader",
   "price": "$60.00",
   "description": "Figura coleccionable Funko de Darth Vader",
   "category": "starwars",
   "id": 2
 }
]
}

```

## Configuración del servidor (server.js)
```
const jsonServer = require('json-server');

const server = jsonServer.create();

const router = jsonServer.router('db.json');

const middlewares = jsonServer.defaults();

const PORT = process.env.PORT || 3000;

server.use(middlewares);

server.use(jsonServer.rewriter({
  '/api/*': '/$1'
}));

server.use(router);

server.listen(PORT, () => {
  console.log(`JSON Server escuchando en puerto ${PORT}`);
});
```

## 📚 Endpoints Disponibles

Método	Endpoint	Descripción
```
GET	/product	Lista todos los productos

GET	/product/:id	Obtiene un producto específico

POST	/product	Crea un nuevo producto

PUT	/product/:id	Actualiza un producto

DELETE	/product/:id	Elimina un producto
```

## Ejemplo de respuesta

```json
[
  {
    "id": 1,
    "name": "Taza Trooper",
    "price": "$60.00",
    "description": "Taza con diseño de casco Trooper",
    "category": "starwars",
    "img": "https://www.claroshop.com/c/star-wars-day/img/categorias/TAZAS_CATEGORIAS_STAR_WARS.png"
  }
]

```

>[!NOTE]
>No olvides hacer commit y push de tus cambios antes de desplegar.
>El primer despliegue puede tardar unos minutos en estar disponible ⏰.
>Revisa los logs de Render en caso de problemas.
>Asegúrate de que el archivo server.js esté en la raíz del proyecto o configura correctamente el path en Render.

🤝 Contribuir
¡Las contribuciones son bienvenidas! Si encuentras un bug o tienes una sugerencia, por favor crea un issue o un pull request.

📄 Licencia
MIT
