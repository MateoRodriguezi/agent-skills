
Y para completar bien la skill, te dejo también un archivo de referencia opcional para copiar en:

`skills/formula-advisor/references/formula-patterns.md`

```markdown
# Patrones comunes de fórmulas

## Lookups
- Buscar un valor exacto
- Buscar con fallback si no existe
- Buscar por múltiples condiciones
- Traer un valor desde otra hoja
- Buscar a la izquierda

## Revenue y métricas
- Sumar revenue neto por período
- Contar transacciones exitosas
- Calcular conversión
- Calcular ticket promedio
- Calcular revenue por país / producto / canal
- Calcular clientes únicos
- Calcular churn simple
- Calcular ARPU / ARPPU
- Calcular MRR simple
- Comparar contra período anterior

## Agregaciones
- SUMIF / SUMIFS
- COUNTIF / COUNTIFS
- AVERAGEIF / AVERAGEIFS
- MAXIFS / MINIFS

## Texto
- Extraer dominio de email
- Separar nombre y apellido
- Limpiar caracteres extraños
- Normalizar mayúsculas / minúsculas
- Reemplazar patrones
- Extraer con regex

## Fechas
- Filtrar por mes
- Calcular fin de mes
- Agrupar por semana
- Comparar fechas
- Calcular días hábiles

## Modernas
- FILTER
- UNIQUE
- SORT
- LET
- ARRAYFORMULA
- QUERY

## Buenas prácticas
- Preferir XLOOKUP en Excel moderno
- Preferir claridad sobre fórmulas “inteligentes”
- Usar helper columns cuando mejora mantenibilidad
- Evitar nested IF monstruosos si hay opciones más limpias