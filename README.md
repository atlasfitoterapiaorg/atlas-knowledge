# atlas-knowledge

Base de conocimiento y plataforma de publicación del Atlas de Fitoterapia.

Este repositorio contiene el conocimiento científico, la estructura editorial, la configuración de Quartz y los componentes necesarios para publicar el Atlas.

La gobernanza, arquitectura, estándares, validadores y plantillas oficiales se mantienen en el repositorio `atlas-core`.

---

## Edición con Obsidian

`atlas-knowledge` puede abrirse directamente como un Vault de Obsidian.

Obsidian funciona como interfaz de edición local y no constituye la fuente de verdad del Atlas.

La fuente oficial del contenido es el repositorio Git, mientras que las plantillas gobernadas permanecen en `atlas-core`.

### Configuración inicial

Abrir como Vault:

```text
atlas-knowledge/
```

El plugin nativo **Templates** deberá estar habilitado.

La configuración del Vault utiliza:

```text
templates
```

como carpeta de plantillas.

Esta configuración se encuentra registrada en:

```text
.obsidian/templates.json
```

### Acceso local a las plantillas gobernadas

Las plantillas oficiales residen en:

```text
atlas-core/30-Plantillas/
```

Para evitar duplicarlas entre repositorios, cada entorno local puede crear un enlace simbólico llamado `templates` dentro de `atlas-knowledge`.

En Windows:

```powershell
cd D:\AtlasFitoterapia\atlas-knowledge

New-Item -ItemType SymbolicLink `
  -Path ".\templates" `
  -Target "..\atlas-core\30-Plantillas"
```

La creación del enlace simbólico puede requerir Developer Mode o ejecutar PowerShell con privilegios de administrador.

El enlace `templates` es una configuración local y no deberá versionarse.

---

## Flujo editorial mínimo

El flujo editorial local es:

```text
atlas-core
    │
    ▼
Plantillas gobernadas
    │
    ▼
Obsidian
    │
    ▼
atlas-knowledge/content
    │
    ▼
Quartz
    │
    ▼
Sitio generado
```

Los documentos creados mediante Obsidian deberán almacenarse dentro de `content/`.

Antes de incorporarse al repositorio deberán respetar los estándares y modelos vigentes del Atlas.

Las estructuras científicas definitivas serán establecidas por el modelo formal de conocimiento correspondiente.

---

## Build local

Para validar la publicación local:

```powershell
npm install
npx quartz build
```

El sitio generado se almacena en:

```text
public/
```

Los archivos generados por Quartz no constituyen contenido fuente del Atlas.

---

## Repositorios relacionados

```text
atlas-core
Gobernanza + arquitectura + estándares + plantillas

atlas-knowledge
Conocimiento + edición + Quartz + publicación
```