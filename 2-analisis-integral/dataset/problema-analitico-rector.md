# Problema analítico rector — Ciclo 2

Este documento **orienta** los análisis de toda la cohorte sobre el dataset compartido, sin
prescribir métodos. Cada doctorando decide qué técnicas aplicar y las justifica; las
diferencias en esas decisiones son el insumo de la revisión entre pares y de la
webconferencia de retroalimentación (Semana 8).

## Pregunta rectora

> **¿Qué explica las diferencias entre poblaciones en su conocimiento, percepción y
> comportamiento de seguridad digital, y qué tan grandes son esas diferencias?**

El dataset captura, para 12.351 personas de 12 países, tres dimensiones del factor humano en
ciberseguridad: **lo que saben** (familiaridad con términos y (mis)concepciones técnicas),
**lo que sienten** (importancia, preocupación, actitudes, riesgo percibido) y **lo que hacen**
(medidas de protección adoptadas, experiencias de victimización). La pregunta rectora invita a
investigar cómo se relacionan estas dimensiones entre sí y cómo varían según el contexto
(país, cultura WEIRD/no-WEIRD, demografía, experiencia en TI).

## Por qué importa para la línea CRIC

La seguridad de infraestructuras y sistemas depende, en última instancia, del comportamiento
de las personas: la mayoría de los incidentes empieza con un factor humano (phishing,
contraseñas débiles, configuraciones inseguras). Entender **qué poblaciones tienen brechas de
conocimiento o prácticas de riesgo, y de qué magnitud**, es un insumo directo para diseñar
defensas, campañas y políticas de ciberseguridad centradas en el usuario — el corazón de la
línea CRIC del DTI.

## Líneas de indagación posibles (no obligatorias, no exhaustivas)

Sirven como punto de partida; puedes formular las tuyas a partir de la exploración. **No** son
un método asignado.

- **Brecha conocimiento–comportamiento.** ¿Saber más de seguridad (`q6`) se traduce en más medidas de protección (`q20`)? ¿O existe una brecha entre lo que la gente sabe y lo que hace?
- **La "paradoja de la privacidad".** ¿Quienes declaran más preocupación (`q18`) o más importancia de proteger sus datos (`q21`) adoptan efectivamente más protecciones (`q20`)?
- **Diferencias culturales (WEIRD vs. no-WEIRD).** ¿Difieren las percepciones de riesgo, las (mis)concepciones o las prácticas entre países occidentales y no occidentales? ¿Qué magnitud tienen esas diferencias?
- **Predictores de victimización.** ¿Qué factores (conocimiento, comportamiento, demografía, uso de internet) se asocian con haber sido víctima de cibercrimen (`q7`)?
- **Estructura latente de las actitudes.** ¿Las baterías de actitud (`q19`) y (mis)concepción (`q9`–`q16`) se agrupan en dimensiones interpretables? ¿Predicen el comportamiento?
- **Perfil del riesgo percibido.** ¿A qué actores (`q22`) se teme más y cómo se relaciona eso con la experiencia real de victimización (`q7`)?

## Orientación metodológica doctoral (transversal a todas las líneas)

Estas indicaciones aplican **cualquiera** sea la técnica que elijas:

1. **Tamaños del efecto e intervalos de confianza son la información primaria; el valor p es secundario.** Con n = 12.351, casi cualquier prueba resultará "estadísticamente significativa". La pregunta doctoral **no** es "¿hay diferencia?" (casi siempre la habrá), sino **"¿de qué tamaño es la diferencia y es sustantivamente relevante?"**. Reporta d de Cohen, η², odds ratios o R² con su intervalo de confianza, e interpreta su magnitud (Cohen, 1988). *Esta es la lección central del entorno* — la misma que ilustró el cuasi-experimento de phishing del Ciclo 1 (efecto significativo pero η² ≈ 0.002, trivial).
2. **Justifica el tratamiento de las escalas.** Decide y argumenta si tratas los ítems Likert como intervalares (paramétrico) u ordinales (no paramétrico), y verifica los supuestos antes de cada prueba.
3. **Documenta la limpieza.** El faltante viene como celda vacía (NaN), no como `9999`; decide cómo tratarlo (exclusión por listas, imputación) y justifícalo. Atiende también la pregunta de control `q13r11`, la inversión de ítems *misconception*, la celda de texto en `q4r8` y el tratamiento de `Ethnicity` (solo EE. UU.). Un análisis exploratorio deficiente compromete todo lo que viene después.
4. **Interpreta en el contexto del problema, no solo en el estadístico.** No basta con "se rechaza H₀": explica qué significa el hallazgo para la seguridad digital de las poblaciones estudiadas.
5. **Reconoce las limitaciones de la muestra.** Las cuotas de representatividad no se alcanzaron plenamente en todos los países (ver README). Declara esta limitación cuando generalices tus hallazgos.

## Lo que este problema rector NO hace

- **No asigna hipótesis.** Formula las tuyas a partir de la exploración (mínimo dos, Semana 6).
- **No prescribe técnicas.** La elección de pruebas, modelos y de la técnica avanzada (Parte 2) es tuya y debe justificarse por los datos y por tu línea de investigación.
- **No fija una única variable dependiente.** Conocimiento, comportamiento, victimización, actitud o preocupación pueden ser el foco según tu pregunta.

---

*Referencias del dataset (citación obligatoria) y del entorno en
[`README.md`](README.md) y [`../../docs/bibliografia.md`](../../docs/bibliografia.md).*
