# SERVAE · Servicios e Infraestructura Aeroportuaria

Guía didáctica e interactiva sobre los servicios e infraestructura de un aeropuerto: qué es cada servicio, dónde ocurre, quién lo presta, con qué equipos y bajo qué normativa (OACI, AFAC y FAA).

**Proyecto académico Cuervos UTVT** · Universidad Tecnológica del Valle de Toluca.

🌐 **Sitio:** https://zer0-hma.github.io/servae/

## Estructura

| Archivo | Para qué sirve |
|---|---|
| `index.html` | Diseño, estilos y lógica del sitio |
| `servicios.json` | Contenido de las fichas técnicas (aquí se agrega la información) |
| `preview.jpg` | Imagen que aparece al compartir el link en redes |
| `robots.txt`, `sitemap.xml` | Ayudan a que buscadores encuentren el sitio |

## Agregar una ficha

Edita `servicios.json` y agrega un objeto nuevo al arreglo, siguiendo la misma estructura que las fichas existentes (`id`, `numero`, `nombreTecnico`, `categoria`, `descripcion`, `equipos`, etc.). El `id` debe ser único y sin espacios, porque se usa en el link directo a la ficha (`#ficha-<id>`).

Las fichas van en el arreglo **en orden de `numero`**. El índice general (144 fichas) se divide en tres categorías:

| Números | Categoría |
|---|---|
| 1–79 | Servicios aeroportuarios |
| 80–135 | Servicios complementarios |
| 136–144 | Servicios comerciales |

Los números que aún no tienen ficha aparecen en el catálogo como "Ficha en elaboración".

Campos que usa el sitio además del contenido:

| Campo | Para qué sirve |
|---|---|
| `ilus` | Número de la ilustración animada que se muestra en la ficha (las ilustraciones viven en `index.html`, en `ILUS`). Si falta, se usa una genérica. |
| `zona` | Zona del mapa del aeropuerto donde aparece la ficha: `pista`, `rodaje`, `plataforma`, `terminal`, `comercios`, `tierra`, `carga`, `combustible`, `hangares`, `heli`, `control`, `sei` o `planta`. |
| `ubicacion.lado` | `aire`, `tierra` o `mixto`; se usa en el filtro del catálogo. |

Campos opcionales: `titulo` (nombre corto para tarjetas y búsqueda), `grupo` (agrupación distinta a `categoria` para el filtro), `secuencia`, `imagen` y `fuente`.

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
