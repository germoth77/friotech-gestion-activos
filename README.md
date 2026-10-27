# FRIOTECH | Gestión y análisis de activos de refrigeración

**Proyecto de portafolio · Versión 1.0 · Excel · Datos 100 % sintéticos**

FRIOTECH es un prototipo de base de datos para administrar una flota demostrativa de equipos de refrigeración comercial, registrar órdenes de trabajo, programar mantenimiento preventivo y analizar costos y fallas.

## Alcance del conjunto de datos

- **200** locales comerciales ficticios distribuidos en cinco regiones simuladas.
- **600** equipos de refrigeración con marca, modelo, número de serie, estado y local asignado.
- **2.100** órdenes de trabajo correctivas y preventivas con fechas, prioridades, horas y costos.
- **25** técnicos ficticios.
- **600** registros de planificación preventiva.
- **240** movimientos históricos de equipos.
- **1.088** registros de uso de repuestos.

## Estructura del Excel

| Hoja | Descripción | Clave |
|---|---|---|
| INICIO | Guía, alcance y reglas de uso | — |
| Locales | Catálogo de puntos comerciales | `ID_Local` |
| Equipos | Inventario maestro | `ID_Equipo` |
| Tecnicos | Catálogo de técnicos | `ID_Tecnico` |
| Ordenes | Historial de intervenciones | `ID_OT` |
| Repuestos | Consumo de repuestos por orden | `ID_Registro` |
| Preventivos | Programación preventiva | `ID_PM` |
| Movimientos | Historial de traslados | `ID_Movimiento` |
| KPIs | Indicadores calculados con fórmulas | — |

## Relaciones recomendadas para Power BI

- `Locales[ID_Local]` 1 → * `Equipos[ID_Local]`
- `Equipos[ID_Equipo]` 1 → * `Ordenes[ID_Equipo]`
- `Tecnicos[ID_Tecnico]` 1 → * `Ordenes[ID_Tecnico]`
- `Ordenes[ID_OT]` 1 → * `Repuestos[ID_OT]`
- `Equipos[ID_Equipo]` 1 → * `Preventivos[ID_Equipo]`
- `Equipos[ID_Equipo]` 1 → * `Movimientos[ID_Equipo]`

**Precaución:** `Ordenes[ID_Local_referencia]` y `Preventivos[ID_Local_referencia]` son campos de referencia. Para un primer modelo de Power BI, usar la relación a través de `Equipos` para evitar rutas ambiguas. Los movimientos representan eventos históricos y no modifican automáticamente la ubicación vigente del inventario.

## Preguntas de negocio

1. ¿Cuántos equipos se encuentran operativos o fuera de servicio?
2. ¿Qué tipos de equipos concentran más órdenes correctivas?
3. ¿Qué locales y regiones generan mayor costo de mantenimiento?
4. ¿Cuántas órdenes siguen abiertas?
5. ¿Qué repuestos aparecen con mayor frecuencia?
6. ¿Cómo evoluciona el volumen de órdenes por mes?

## Uso

1. Descargar `FRIOTECH_PORTAFOLIO_200_LOCALES_600_EQUIPOS.xlsx`.
2. Abrir la hoja `INICIO` y revisar el diccionario resumido.
3. Revisar `KPIs` para consultar indicadores formulados en Excel.
4. En Power BI Desktop, elegir **Obtener datos > Excel** e importar `Locales`, `Equipos`, `Tecnicos`, `Ordenes`, `Repuestos`, `Preventivos` y `Movimientos`.
5. Revisar tipos de datos y crear las relaciones anteriores en la vista Modelo.

## Próximas mejoras

- Dashboard interactivo en Power BI con análisis por fecha, región, local, tipo de equipo y falla.
- Normalización adicional de catálogos de fallas, modelos y repuestos.
- Reglas de calidad de datos y controles de integridad.
- Aplicación web/móvil para registrar intervenciones y actualizar inventario.

## Aviso de privacidad y transparencia

**Todos los nombres de locales, técnicos, equipos, registros, fechas y costos son ficticios, generados exclusivamente con fines educativos y de portafolio.** No se utilizan datos de clientes, empleados ni sistemas internos de Arca Continental. Este proyecto personal no está afiliado ni implementado por esa empresa.

## Autor

Luis Germán Aguirre Castillo · [Portafolio](https://germoth77.github.io/) · [GitHub](https://github.com/germoth77)
