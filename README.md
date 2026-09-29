# AE1 — Flujo colaborativo con Git y GitHub

Práctica de la asignatura DPL para trabajar con Git y GitHub utilizando ramas, issues, pull requests, resolución de conflictos, tags y releases.

## Entorno utilizado

La práctica se ha realizado de forma individual utilizando dos copias locales del proyecto:

- `ae1`: repositorio principal, utilizado como user1.
- `ae1-user2`: segunda copia local, utilizada para simular user2.
- `git-work`: repositorio principal en GitHub.
- `git-work-espejo`: repositorio espejo utilizado para la modalidad individual.

Repositorio principal:

https://github.com/mariaizdo05/git-work

## Preparación del repositorio

Primero se creó el repositorio `git-work` en GitHub con README y licencia MIT.

Después se creó `git-work-espejo`, que se utilizó como repositorio auxiliar para simular el trabajo de un segundo usuario.

Los repositorios remotos se configuraron mediante SSH.

## Página inicial

Se añadieron los siguientes archivos:

- `index.html`
- `css/cover.css`
- `.gitignore`

La página se personalizó posteriormente desde la rama `custom-text`.

## Documentación y GitHub Actions

Se configuró MkDocs mediante:

- `mkdocs.yml`
- `docs/index.md`

También se creó el workflow:

`.github/workflows/ci.yml`

El workflow ejecuta:

`mkdocs build --strict`

para comprobar automáticamente que la documentación se construye correctamente.

## Primera issue y pull request

Se creó la issue:

`Add custom text for startup contents`

Para resolverla se creó la rama:

`custom-text`

En ella se modificaron el nombre, el eslogan y el contenido de la portada.

Durante la revisión también se modificó el pie de página y se ajustó nuevamente el eslogan.

Finalmente el pull request se fusionó con `main` y la issue quedó cerrada.

## Segunda issue y conflicto

Se creó la issue:

`Improve UX with cool colours`

En el repositorio principal se hizo un cambio local del color del botón a `purple` sin subirlo al remoto.

Desde la segunda copia del repositorio se creó la rama:

`cool-colors`

En ella se cambió la misma propiedad a:

`darkgreen`

Al fusionar posteriormente `cool-colors` con el `main` local apareció un conflicto en:

`css/cover.css`

El conflicto se resolvió manualmente conservando:

`color: darkgreen;`

Después se añadió:

`text-shadow: 2px 2px 8px lightgreen;`

La issue quedó cerrada al incluir `Closes #3` en el mensaje del commit.

## Problemas encontrados

### Autenticación con GitHub

Al principio intenté hacer `git push` utilizando HTTPS y GitHub rechazó la contraseña.

Se solucionó generando una clave SSH y cambiando los remotos al formato:

`git@github.com:usuario/repositorio.git`

### Error de MkDocs

El primer workflow de GitHub Actions falló porque `docs/index.md` contenía un enlace relativo a `../index.html`.

Como MkDocs se ejecutaba con `--strict`, el warning hacía fallar la construcción.

Se sustituyó el enlace relativo por la dirección del archivo en GitHub y el workflow terminó correctamente.

### Conflicto en cover.css

Las ramas modificaron la misma línea de `css/cover.css` con colores diferentes.

Git mostró los marcadores de conflicto y se resolvió manualmente dejando `darkgreen`.

## Versión

Se creó el tag:

`0.1.0`

y posteriormente se publicó la Release `0.1.0` en GitHub.

## Resultado

Al finalizar la práctica se utilizaron:

- ramas
- commits
- repositorios remotos
- issues
- pull requests
- GitHub Actions
- resolución de conflictos
- tags
- releases
- MkDocs