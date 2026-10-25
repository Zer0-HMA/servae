# SERVAE · Servicios e Infraestructura Aeroportuaria

Guía didáctica e interactiva sobre los servicios e infraestructura de un aeropuerto: qué es cada servicio, dónde ocurre, quién lo presta, con qué equipos y bajo qué normativa (OACI, AFAC y FAA).

**Proyecto académico Cuervos UTVT** · Universidad Tecnológica del Valle de Toluca.

🌐 **Sitio:** https://zer0-hma.github.io/servae/

## Estructura

| Archivo | Para qué sirve |
|---|---|
| `index.html` | Diseño, estilos y lógica del sitio |
| `servicios.json` | Contenido de las fichas técnicas (aquí se agrega la información) |
| `img/fichas/` | Infografías de las fichas 01–23 (sección 8, Recursos visuales) |
| `preview.jpg` | Imagen que aparece al compartir el link en redes |
| `robots.txt`, `sitemap.xml` | Ayudan a que buscadores encuentren el sitio |

## Agregar una ficha

Edita `servicios.json` y agrega un objeto nuevo al arreglo, siguiendo la misma estructura que las fichas existentes (`id`, `numero`, `nombreTecnico`, `categoria`, `descripcion`, `equipos`, etc.). El `id` debe ser único y sin espacios, porque se usa en el link directo a la ficha (`#ficha-<id>`).

Las fichas van en el arreglo **en orden de `numero`**, que es el orden del índice general (01 Pistas de aterrizaje y despegue, 02 Calles de rodaje, …).

Campos opcionales:

| Campo | Para qué sirve |
|---|---|
| `titulo` | Nombre corto del índice (p. ej. "Áreas de migración"); se muestra en tarjetas y búsqueda. Si falta, se usa `nombreTecnico`. |
| `grupo` | Grupo general para el filtro del catálogo (Infraestructura aeroportuaria, Servicios al pasajero, …). La `categoria` original del equipo se sigue mostrando dentro de la ficha. |
| `secuencia` | Lista de pasos de la secuencia operativa; aparece en la sección 8. |
| `imagen` | Ruta a una imagen en `img/fichas/` (de preferencia `.webp`); aparece en la sección 8. |
| `fuente` | Fuente de la información; aparece al final de la normativa. |

Los campos vacíos (`""`) no se muestran en la ficha.

Antes de subir, puedes validar que el JSON no tenga errores con:

```bash
python -m json.tool servicios.json > /dev/null && echo "JSON válido"
```

## Probar localmente

El sitio carga `servicios.json` con `fetch()`, así que no funciona abriendo el archivo directo; necesita un servidor:

```bash
python -m http.server 8000
```

Y abre http://localhost:8000

## Aviso

Material didáctico. No sustituye la normativa vigente; verifica siempre la edición actual de cada disposición.
