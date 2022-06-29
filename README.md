# Componentes para Dziro.

> Biblioteca de componentes para dziro app

## Preview 
Para ver un preview de los componentes así como ejemplos de uso puede correr el siguiente comando.
```bash
npm run dev
```

## Tipografías
Debe instalar en su proyecto las siguientes tipografías para que los estilos sean correctos.
- Raleway
- Ropa sans

```html
<head>
  ...
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Raleway&family=Ropa+Sans&display=swap" rel="stylesheet">
  ...
</head>
```

## Iconos
Debe copiar la fuente de íconos y llevarla a su proyecto para que se vean correctamente y agregar el css a su index.html
``` bash
$ cp -r ./public/icons/ <your_path>
```

```html
<head>
  ...
  <link rel="stylesheet" href="/icons/style.css">
  ...
</head>
```

