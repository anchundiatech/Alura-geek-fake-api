

# Alura Geek Fake API

API REST simulada para el proyecto Alura Geek, ideal para pruebas y prototipos de e-commerce. Implementada con [JSON Server](https://github.com/typicode/json-server) y desplegada en [Vercel](https://vercel.com).

![Vercel](https://img.shields.io/badge/Deploy-Vercel-black?logo=vercel)

## 🚀 Demo

[alurageek-api.vercel.app](https://alurageek-api.vercel.app/)

## ✨ Características

- API REST lista para usar, sin backend real
- Endpoints para productos y categorías
- CRUD completo
- Despliegue automático en Vercel

## ⚡ Inicio Rápido

1. Haz click en "**Use this template**" o clona este repositorio
2. Actualiza el archivo [`db.json`](./db.json) con tus datos
3. Crea una cuenta o inicia sesión en [Vercel](https://vercel.com)
4. En el dashboard de Vercel, haz click en "**+ New Project**" e "**Import**" tu repositorio
5. En la pantalla "**Configure Project**", deja todo por defecto y haz click en "**Deploy**"
6. Espera a que el despliegue se complete y ¡tu API estará lista para usar! 🎉

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

## Creación Paso a Paso



### Step 1

Create a new repository, for example, **alurageek-API**. Then clone that empty repository.

### Step 2

You need to run the npm init command:
```
npm init -y
```

This will generate a **package.json**. Now, what you need to do is change these lines:

Change this line:
```
 "main": "index.js",
```

To this:

```
  "main": "api/server.js",
```

And this:

```
"test": "echo \"Error: no test specified\" && exit 1"
```

To this:

```
"start": "node api/server.js"
```

### Step 3

Now it's time to run the command:

```
npm install json-server cors
```

![Alt text](image.png)

You'll see that both **cors** and ***json-server*** have been added to the package.json.

### Step 4

Run the command:

```
npm install json-server
```

Add the ***.gitignore*** file and add ***node_modules***.

### Paso 5: Configuración del Servidor

1. Crea una carpeta **api**
2. Dentro de la carpeta api, crea el archivo **server.js**:

```javascript
// Configuración del servidor JSON Server
const jsonServer = require('json-server')
const server = jsonServer.create()
const router = jsonServer.router('db.json')
const middlewares = jsonServer.defaults()

server.use(middlewares)
// Configuración de rutas
server.use(jsonServer.rewriter({
    '/api/*': '/$1',
    '/product/:resource/:id/show': '/:resource/:id'
}))
server.use(router)
server.listen(3000, () => {
    console.log('JSON Server está funcionando')
})

// Exportar el servidor
module.exports = server
```

### Paso 6: Configuración de Vercel

Crea el archivo **vercel.json** en la raíz del proyecto:

```json
{
  "functions": {
    "api/server.js": {
      "memory": 1024,
      "includeFiles": "db.json"
    }
  },
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "api/server.js"
    }
  ]
}
```

## Notas Importantes

- No olvides hacer commit y push de tus cambios antes de desplegar
- El primer despliegue puede tardar unos minutos en estar disponible ⏰
- Si encuentras algún problema, revisa los logs en tu dashboard de Vercel


## 📚 Endpoints Disponibles

| Método | Endpoint           | Descripción                      |
|--------|--------------------|----------------------------------|
| GET    | /product           | Lista todos los productos        |
| GET    | /product/:id       | Obtiene un producto específico   |
| POST   | /product           | Crea un nuevo producto           |
| PUT    | /product/:id       | Actualiza un producto            |
| DELETE | /product/:id       | Elimina un producto              |

### Ejemplo de respuesta

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


## 🤝 Contribuir

¡Las contribuciones son bienvenidas! Si encuentras un bug o tienes una sugerencia, por favor crea un issue o un pull request.

## 📄 Licencia

MIT
