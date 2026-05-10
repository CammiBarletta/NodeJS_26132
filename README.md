# CLI FakeStore API

Aplicación de línea de comandos en Node.js que consume la [FakeStore API](https://fakestoreapi.com).

## Requisitos

- Node.js v18 o superior

## Instalación

```bash
git clone 
cd pre-entrega
```

## Uso

### Obtener todos los productos

```bash
npm run start GET products
```

### Obtener un producto por ID

```bash
npm run start GET products/1
```

### Crear un producto

```bash
npm run start POST products <title> <price> <category>
```

Ejemplo:

```bash
npm run start POST products Remera-Rex 500 ropa
```

### Eliminar un producto

```bash
npm run start DELETE products/5
```

## Tecnologías

- Node.js
- Fetch API (nativa)
- FakeStore API
