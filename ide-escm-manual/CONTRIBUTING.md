# Cómo colaborar en este manual

Somos dos personas en lugares distintos actualizando el mismo repo. Para
no pisarnos el trabajo, seguimos estas reglas simples.

## Regla de oro

**Antes de escribir, `git pull`. Después de escribir, commit chico y
`git push` seguido** (no dejar cambios sin subir por días). Como cada
persona normalmente edita capítulos distintos, los conflictos deberían
ser raros — pero si dos tocan el mismo archivo el mismo día, avisarse por
mensaje antes.

## Flujo de trabajo

```bash
# 1. Antes de empezar a editar, traer lo último
git pull origin main

# 2. Editar o crear el/los capítulo(s) que corresponda

# 3. Guardar el avance en la bitácora (docs/99-bitacora.md)
#    - qué se hizo, quién, fecha

# 4. Commit con mensaje claro
git add .
git commit -m "docs: agrega capítulo de autenticación de capas restringidas"

# 5. Subir
git push origin main
```

Si preferís no trabajar directo sobre `main`, la alternativa es rama por
persona y Pull Request:

```bash
git checkout -b avance/leonardo-autenticacion
# ... editar ...
git commit -m "docs: agrega capítulo de autenticación"
git push origin avance/leonardo-autenticacion
# Abrir Pull Request en GitHub y mergear
```

Para un manual de dos personas, el flujo directo sobre `main` con pull
frecuente suele alcanzar; las ramas convienen si empiezan a trabajar más
gente o si quieren revisar el texto antes de que quede "oficial".

## Convención de nombres de archivo

- `docs/NN-titulo-corto.md`, con `NN` como número de dos dígitos en
  orden de lectura (no de fecha).
- Si un capítulo se divide en partes, usar `NNb-titulo.md`,
  `NNc-titulo.md`, etc., en vez de renumerar todo lo que sigue.
- Nombres en minúscula, con guiones, sin tildes ni espacios.

## Estructura de un capítulo nuevo

Cada capítulo empieza con una cabecera de navegación y termina igual,
para poder moverse sin volver siempre al índice:

```markdown
[⬅ Índice](../README.md) · [Capítulo anterior](0X-anterior.md) · [Capítulo siguiente](0X-siguiente.md)

# N. Título del capítulo

_Última actualización: DD/MM/AAAA — nombre_

...contenido...

---
[⬅ Índice](../README.md) · [Capítulo anterior](0X-anterior.md) · [Capítulo siguiente](0X-siguiente.md)
```

## Al agregar un capítulo

1. Crear el archivo en `docs/`.
2. Sumar la fila en la tabla de índice del `README.md` de la raíz.
3. Agregar una entrada en [docs/99-bitacora.md](docs/99-bitacora.md)
   (fecha, quién, qué se agregó/cambió).
4. Si el capítulo reemplaza contenido de otro (por ejemplo, "Seguridad"
   se separa en "Autenticación" + "HTTPS"), dejar una nota al pie en el
   capítulo viejo apuntando al nuevo, en vez de borrar sin dejar rastro.

## Diagramas

GitHub renderiza [Mermaid](https://mermaid.js.org/) nativo dentro de los
bloques \`\`\`mermaid — no hace falta generar imágenes aparte. Ya hay un
ejemplo en [docs/02-arquitectura.md](docs/02-arquitectura.md).

## Bitácora

`docs/99-bitacora.md` es de solo agregar (no se reescribe lo viejo). Cada
entrada nueva va **arriba** de todo, formato:

```markdown
## DD/MM/AAAA — Nombre

- Qué se hizo
- Qué quedó pendiente / próximo paso
```
