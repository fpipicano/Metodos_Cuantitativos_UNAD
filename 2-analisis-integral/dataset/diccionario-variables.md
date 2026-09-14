# Diccionario de variables

Diccionario **curado y orientado al análisis** del dataset *Digital Security Perceptions &
Practices in 12 Countries*. Agrupa las ~200 columnas por bloque temático, indica escala,
códigos de valor y señala las variables más útiles para cada tipo de análisis del Ciclo 2.

> La **redacción literal** de cada ítem está en el `DataMap` oficial de los autores. Aquí se
> prioriza la estructura analítica: convención de nombres, escalas, códigos perdidos y rol
> potencial de cada bloque.

## Convenciones

- **Nombres de columna:** los bloques con subítems usan el patrón `Q{n}r{m}` (p. ej. `Q6r3` = bloque Q6, ítem 3). Un bloque = un tema; cada `r{m}` = un ítem.
- **Código de no-respuesta `9999`:** aparece como "prefiero no responder" en demografía, `Q7`, `Q25` y `Q26`, y como "no entiendo la afirmación" en las baterías Likert `Q9`–`Q19` (incluidas `Q17`, `Q18` y `Q19`). **`Q22` no tiene este código.** Convertir a NaN antes de analizar.
- **Binarias de selección múltiple:** `0` = no marcado, `1` = marcado.
- **`[Ethnicity]`** solo tiene datos válidos para la submuestra de **EE. UU.**

> ⚠️ **Errata del data map oficial.** El data map etiqueta el ítem "Tor network" como `Q6r8`,
> pero por su posición en la batería corresponde a `Q6r18`. **Confía siempre en los encabezados
> reales del CSV** (`df.columns`), no en la numeración impresa del data map, y verifica el
> contenido de cada ítem antes de construir índices.

## Identificadores y demografía

| Variable | Descripción | Escala / códigos | Rol analítico |
|---|---|---|---|
| `ID` | Numeración consecutiva del participante | entero | identificador |
| `Country` | País | 1=China, 2=Alemania, 3=India, 4=Israel, 5=Italia, 6=México, 7=Polonia, 8=Arabia Saudita, 9=Sudáfrica, 10=Suecia, 11=Reino Unido, 12=EE.UU. | **factor clave** (12 grupos; base del corte WEIRD/no-WEIRD) |
| `Gender` | Género | 1=Masc., 2=Fem., 3=No binario, 4=autodescripción, 9999=NR | factor |
| `Gender_SelfDescription` | Autodescripción de género | texto libre | cualitativa |
| `Age` | Rango de edad | 1=18–24, 2=25–39, 3=40–54, 4=55+ | ordinal |
| `Education` | Nivel educativo | 1=Bajo, 2=Medio, 3=Alto, 4=Otro | ordinal |
| `Ethnicity` | Raza (**solo EE. UU.**) | 1=Blanca, 2=Afroamericana, 3=Hispana/Latina, 4=Asiática, 5=Otra | factor (US) |

## Uso de tecnología (contexto)

| Bloque | Tema | Ítems | Escala |
|---|---|---|---|
| `Q1r1`–`Q1r7` | Dispositivos usados a diario (smartphone, PC, laptop, tablet, altavoz, wearable, ninguno) | 7 | binaria 0/1 |
| `Q2r1`–`Q2r3` | Dispositivos de hogar inteligente (energía, seguridad, hogar/jardín) | 3 | 1=Sí, 2=No, 3=No estoy seguro |
| `Q3r1`–`Q3r13` | Frecuencia de uso de internet por propósito (compras, banca, salud, etc.) | 13 | 1=Nunca … 8=Varias veces al día |
| `Q4r1`–`Q4r8` | Frecuencia de canales de comunicación (llamadas, video, SMS, messenger, redes, email, foros) | 8 | 1=Nunca … 8=Varias veces al día |

## Conocimiento y experiencia

| Bloque | Tema | Ítems | Escala | Rol analítico |
|---|---|---|---|---|
| `Q6r1`–`Q6r22` | **Familiaridad con términos** (malware, ransomware, phishing, 2FA, HTTPS, VPN, Tor, etc.) | 22 | 1=Nunca oído … 5=Sé muy bien cómo funciona | índice de **conocimiento** (candidato a VD continua o a PCA/factorial) |
| `Q7r1`–`Q7r9` | **Víctima de cibercrimen** (malware, phishing, ransomware, ciberacoso, fraude, etc.) | 9 | 1=Sí, 2=No, 9999=NR | **variable binaria natural** → regresión logística (Semana 8) |
| `Q8r1`–`Q8r10` | Fuentes de información sobre seguridad | 10 (+texto `Q8r10oer1`) | binaria 0/1 | comportamiento |

## Concepciones y (mis)concepciones — baterías Likert de acuerdo

Todas en escala **1=totalmente en desacuerdo … 5=totalmente de acuerdo** (`9999`=no entiende).
⚠️ **Muchos ítems son afirmaciones falsas (misconceptions):** en esos, mayor acuerdo = *menor*
conocimiento real. **Identifica e invierte** los ítems inversos antes de construir índices.

| Bloque | Tema | Ítems |
|---|---|---|
| `Q9r1`–`Q9r9` | Cifrado extremo a extremo (E2EE, WhatsApp/Signal) | 9 |
| `Q10r1`–`Q10r5` | HTTPS / navegación segura | 5 |
| `Q11r1`–`Q11r5` | Redes WLAN públicas | 5 |
| `Q12r1`–`Q12r8` | VPN y red Tor | 8 |
| `Q13r1`–`Q13r18` | Contraseñas y procesos de login (incluye 2FA, biometría) | 18 |
| `Q14r1`–`Q14r9` | Seguridad de dispositivos finales | 9 |
| `Q15r1`–`Q15r16` | Malware y engaño en internet | 16 |
| `Q16r1`–`Q16r6` | Modo incógnito / navegación privada | 6 |

> **Pregunta de control:** `Q13r11` **no** mide seguridad — pide marcar una opción específica
> ("la segunda opción desde la derecha / desde abajo"). Sirve para **detectar respuestas de
> baja calidad**. Úsala para filtrar y **documenta tu criterio de exclusión**; no la incluyas
> en ningún índice de conocimiento.

## Importancia, preocupación y actitudes

Escalas 1–5; `9999` = "no entiendo la afirmación" (aplica a `Q17`, `Q18` y `Q19`).

| Bloque | Tema | Ítems | Escala |
|---|---|---|---|
| `Q17r1`–`Q17r15` | Importancia de **prevenir** amenazas (malware, fraude, acceso no autorizado, etc.) | 15 | 1=Nada … 5=Muy importante |
| `Q18r1`–`Q18r8` (Q18A) | **Preocupación** por comunicaciones, WLAN, ubicación, biometría | 8 | 1=Nada … 5=Muy preocupado |
| `Q18r9`–`Q18r19` (Q18B) | **Preocupación** por contraseñas, equipo, malware, asistentes de voz | 11 | 1=Nada … 5=Muy preocupado |
| `Q19r1`–`Q19r8` (Q19A) | **Actitudes** hacia privacidad/cifrado ("nada que ocultar", etc.) | 8 | 1=Totalmente en desacuerdo … 5=Totalmente de acuerdo |
| `Q19r9`–`Q19r19` (Q19B) | **Actitudes**: ventajas del cifrado, fatalismo, molestia, usabilidad | 11 | 1–5 |

## Comportamiento protector y valor de los datos

| Bloque | Tema | Ítems | Escala | Rol analítico |
|---|---|---|---|---|
| `Q20r1`–`Q20r14` | **Medidas de protección usadas** (updates, backups, antivirus, 2FA, VPN, gestor de contraseñas, etc.) | 14 | binaria 0/1 | índice de **comportamiento protector** (suma 0–14 → VD continua) |
| `Q21r1`–`Q21r15` | Importancia de proteger tipos de dato (nombre, dirección, salud, biometría, contraseñas, etc.) | 15 | 1=Nada … 5=Muy importante | valor percibido |
| `Q22r1`–`Q22r8` | Riesgo percibido por actor (familia, colegas, gobierno propio/extranjero, empresas, criminales, hackers) | 8 | 1=Nada … 5=Muy probable (**sin código 9999**) | percepción de amenaza |

## Variables de segmentación adicionales

| Variable | Descripción | Códigos |
|---|---|---|
| `Q25` | Experiencia práctica en informática / TI (trabajo o formación) | 1=Sí, 2=No, 9999=NR |
| `Q26` | Trasfondo migratorio | 1=Sí, 2=No, 9999=NR |

## Variables sugeridas por tipo de análisis

- **Comparación de grupos (Semana 6):** `Country` (12 grupos → ANOVA/Kruskal-Wallis); corte WEIRD vs. no-WEIRD, `Q25`, `Q26`, `Gender` (2–3 grupos → t-test/Mann-Whitney).
- **Regresión lineal múltiple (Semana 7):** VD continua = índice de conocimiento (Q6) o comportamiento protector (suma Q20); predictores = demografía + `Q25` + uso de internet (Q3).
- **Regresión logística (Semana 8):** VD binaria natural = cualquier ítem de `Q7` (víctima de cibercrimen Sí/No); o dicotomizar un índice con umbral justificado.
- **Multivariante / SEM / factorial (Parte 2, Opción 1):** las baterías Likert (Q6, Q9–Q19) son candidatas naturales a PCA/AFE/AFC; modelo estructural plausible: actitudes (Q19) → comportamiento (Q20), con conocimiento (Q6) como antecedente.
- **Inferencia bayesiana (Parte 2, Opción 3):** reformular en PyMC cualquiera de las comparaciones o regresiones de la Parte 1.
- **Evaluación estadística de ML (Parte 2, Opción 4):** clasificación de victimización (`Q7`) o de adopción de una medida (`Q20`) con ≥3 clasificadores.
- **Series temporales (Parte 2, Opción 2):** **no aplicable** a este dataset, que es transversal y no tiene variable de tiempo.

---

*La redacción íntegra de cada ítem está en el `DataMap` oficial de los autores. Cualquier
decisión de recodificación (inversión de ítems, umbrales, exclusiones por la pregunta de
control) debe documentarse en el notebook.*
