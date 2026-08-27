# AGENTS.md

## Propósito

Este repositorio contiene el conocimiento científico y editorial del Atlas de Fitoterapia.

Las reglas normativas, arquitectónicas y de validación se encuentran en el repositorio hermano:

```text
../atlas-core
```

Antes de crear o modificar conocimiento, Codex y cualquier agente automatizado deberán consultar las instrucciones de:

```text
../atlas-core/AGENTS.md
```

y respetar los documentos GOV, ADR, ADM y EEA aplicables.

---

## Fuente de verdad

La identidad y estructura del conocimiento no dependen de:

- nombres de archivo;
- carpetas;
- Obsidian;
- Quartz;
- GitHub Pages.

Las entidades y relaciones deberán cumplir:

```text
../atlas-core/tools/schemas/entities.yaml
../atlas-core/tools/schemas/relationships.yaml
```

y las reglas correspondientes de `atlas-core`.

---

## Reconciliación

Antes de crear una entidad nueva:

1. buscar si ya existe en este repositorio;
2. reutilizar su ID cuando represente el mismo concepto;
3. evitar duplicados semánticos;
4. crear una entidad nueva sólo cuando sea realmente necesaria.

---

## Estado inicial

Todo conocimiento generado automáticamente deberá iniciar como:

```yaml
governance_status: proposed
```

Los agentes no deberán aprobar automáticamente contenido nuevo.

---

## Relaciones

Las relaciones estructuradas deberán almacenarse en Front Matter.

Ejemplo:

```yaml
relationships:
  - type: posee_parte
    target: PVE-000001
```

Sólo podrán utilizarse relaciones reconocidas por:

```text
../atlas-core/tools/schemas/relationships.yaml
```

---

## Wikilinks

Toda relación útil para navegación humana deberá tener también representación mediante wikilink cuando corresponda.

Ejemplo:

```markdown
[[../partes-vegetales/rizoma|Rizoma]]
```

Las dos representaciones cumplen funciones distintas:

```text
relationships
→ agentes
→ validación
→ grafo semántico

wikilinks
→ Obsidian
→ Quartz
→ backlinks
→ grafo visual
```

Deberán mantenerse coherentes.

---

## Obsidian

Este repositorio puede abrirse directamente como Vault de Obsidian.

Obsidian se utilizará para:

- revisar entidades;
- navegar relaciones;
- inspeccionar backlinks;
- identificar nodos aislados;
- visualizar el grafo local;
- realizar correcciones editoriales.

Los agentes deberán generar Markdown compatible con Obsidian.

No deberán depender de plugins específicos para que el conocimiento siga siendo comprensible.

---

## Quartz

Este repositorio contiene también la capa de publicación mediante Quartz.

Los agentes deberán preservar compatibilidad con:

- wikilinks;
- Markdown;
- Front Matter;
- navegación;
- backlinks;
- grafo;
- build de Quartz.

No deberán modificar configuración de Quartz salvo que la tarea lo requiera explícitamente.

---

## Publicación

El flujo esperado es:

```text
Agente
   ↓
atlas-knowledge
   ↓
validación
   ↓
revisión en Obsidian
   ↓
merge
   ↓
Quartz
   ↓
GitHub Pages
```

La generación de contenido no implica automáticamente su publicación.

---

## Validación obligatoria

Antes de considerar terminada una tarea de conocimiento deberá ejecutarse desde este repositorio:

```powershell
py ..\atlas-core\tools\validate_entities.py .
```

El resultado deberá indicar:

```text
VALIDACIÓN CORRECTA
Integridad referencial: correcta
```

Si el agente creó el error, deberá intentar corregirlo antes de finalizar.

---

## Integridad del grafo

Antes de terminar una tarea deberán comprobarse:

```text
✓ IDs válidos
✓ sin duplicados
✓ relaciones reconocidas
✓ targets existentes
✓ origen y destino compatibles
✓ wikilinks coherentes
✓ procedencia disponible cuando corresponda
✓ ausencia de nodos aislados accidentales
```

Un nodo podrá permanecer aislado únicamente cuando exista una razón legítima.

---

## Procedencia

La información científica obtenida desde fuentes externas deberá mantener trazabilidad.

Cuando estén disponibles deberán conservarse:

- fuente;
- DOI;
- PMID;
- identificadores externos;
- URL;
- edición o versión;
- fecha de consulta;
- contexto relevante.

No deberán inventarse datos faltantes.

---

## Regla de no inferencia

No deberá inferirse automáticamente conocimiento entre entidades relacionadas.

Ejemplos:

```text
compuesto presente en rizoma
≠
compuesto presente en toda la planta
```

```text
efecto observado en extracto
≠
efecto demostrado para todo el taxón
```

```text
uso tradicional
≠
uso terapéutico validado
```

---

## Trabajo de Codex

Cuando una tarea solicite incorporar una planta o ampliar conocimiento, Codex deberá intentar completar el flujo:

```text
buscar
↓
reconciliar
↓
crear entidades faltantes
↓
asignar IDs
↓
crear relaciones
↓
incorporar procedencia
↓
generar wikilinks
↓
validar
↓
corregir
↓
entregar cambios revisables
```

El objetivo es minimizar creación manual de archivos.

---

## Curcuma longa

El piloto actual del Atlas utiliza:

```text
TAX-FAM-000001 → Zingiberaceae
TAX-GEN-000001 → Curcuma
TAX-SP-000001  → Curcuma longa L.
PVE-000001     → Rizoma
```

Estas entidades deberán reutilizarse y no recrearse durante el piloto.

---

## Criterio de terminado

Una incorporación automatizada de conocimiento estará terminada cuando:

```text
✓ entidades creadas o reconciliadas
✓ relaciones gobernadas
✓ procedencia conservada
✓ validación correcta
✓ navegación Obsidian funcional
✓ contenido preparado para Quartz
✓ grafo visual conectado
```