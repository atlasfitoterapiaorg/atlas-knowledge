# AGENTS.md

## Alcance

Este repositorio contiene las entidades de conocimiento del Atlas, sus relaciones, procedencia y representaciones editoriales en Markdown. También integra la revisión humana mediante Obsidian y la publicación mediante Quartz.

Antes de modificar conocimiento, los agentes deberán leer `../atlas-core/AGENTS.md` y consultar los GOV, ADR, ADM y EEA que allí se indiquen como aplicables. Las reglas normativas y operativas centrales no se duplican en este archivo.

## Reglas específicas de `atlas-knowledge`

- reconciliar cada entidad contra el conocimiento existente antes de crearla y reutilizar su ID cuando represente el mismo concepto;
- usar sólo los tipos de `../atlas-core/tools/schemas/entities.yaml`, las relaciones y pares de `../atlas-core/tools/schemas/relationships.yaml` y los IDs definidos conforme a EEA-002;
- iniciar en `governance_status: proposed` todo conocimiento generado automáticamente;
- conservar procedencia verificable, límites, contextos y contradicciones sin inventar datos ni propagar propiedades entre taxones, partes vegetales, drogas, preparados, compuestos, usos, actividades o evidencia;
- mantener coherencia entre las relaciones gobernadas del Front Matter y los wikilinks utilizados por Obsidian y Quartz;
- no modificar GOV, ADR, ADM, EEA, schemas o validadores durante tareas científicas ordinarias;
- corregir los errores provocados por los propios cambios y dejar el árbol revisable, sin publicar automáticamente.

## Calidad editorial de las entidades

El Front Matter está orientado a máquinas; el cuerpo Markdown, a personas. Los campos `id`, `type`, `governance_status`, `relationships`, `external_ids`, `provenance` y demás propiedades estructuradas no deberán convertirse mecánicamente en secciones visibles.

Reglas operativas:

- no crear secciones vacías ni placeholders como “Pendiente de incorporación”, “Pendiente de validación”, “Sin información” o equivalentes;
- conservar listas estructurales vacías cuando el schema las requiera, pero omitir sus secciones editoriales si no aportan contenido;
- explicar qué es cada entidad de forma independiente de la fuente o del proceso que motivó su creación;
- identificar toda fuente citada mediante entidad, autor y año, DOI, PMID o enlace, sin referencias ambiguas;
- exponer la procedencia útil de forma legible y preferir el wikilink a una entidad `publication` existente;
- asegurar que cada párrafo defina, describa, contextualice, explique una relación, resuma evidencia, presente procedencia o facilite navegación;
- conservar incertidumbre científicamente relevante sin rellenar vacíos ni repetir literalmente el Front Matter.

## Curcuma longa

El piloto reutiliza, entre otras, estas entidades existentes:

```text
TAX-FAM-000001 → Zingiberaceae
TAX-GEN-000001 → Curcuma
TAX-SP-000001  → Curcuma longa L.
PVE-000001     → Rizoma
```

No deberán recrearse ni recibir IDs nuevos.

## Validación y entrega

Antes de terminar, ejecutar desde este repositorio:

```powershell
py ..\atlas-core\tools\validate_entities.py .
```

Además, revisar IDs duplicados, relaciones no autorizadas, targets inexistentes, wikilinks rotos, nodos aislados accidentales, procedencia y compatibilidad con Obsidian y Quartz. La entrega deberá enumerar cambios, validaciones, limitaciones y decisiones pendientes de revisión humana.
