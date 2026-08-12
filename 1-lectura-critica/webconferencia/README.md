# Webconferencia de modelamiento — Ciclo 1 · Semana 2

Material del **tutor** para la **webconferencia de modelamiento** (Semana 2 del Ciclo 1). En
esta sesión el tutor realiza **en vivo** el análisis metodológico completo de un artículo
empírico publicado, mostrando el proceso de pensamiento que el doctorando **replicará de
forma autónoma en la Semana 3** sobre un artículo distinto del [banco](../articulos/).

> Esta carpeta **no** forma parte del banco de artículos seleccionables por los estudiantes.
> Es el caso de demostración común para toda la cohorte.

## Artículo de la sesión

**Chen, S., & Ye, J. (2023).** *Understanding consumers' intentions to purchase smart clothing
using PLS-SEM and fsQCA.* PLOS ONE, 18(9), e0291870.
[https://doi.org/10.1371/journal.pone.0291870](https://doi.org/10.1371/journal.pone.0291870)

- **Acceso:** Open Access — **Creative Commons Attribution (CC BY)**. Por eso el PDF **sí** puede incluirse en este repositorio (a diferencia del banco, cuyos artículos son de acceso restringido y se enlazan por DOI).
- **Archivo:** coloca aquí el PDF como `Chen-Ye-2023-smart-clothing-PLS-SEM-fsQCA.pdf`.
- **Diseño en breve:** encuesta transversal correlacional · n = 225 consumidores chinos · muestreo bola de nieve (WeChat) · 7 constructos latentes (FUN, EXP, AES, PU, PEOU, ATT, PI) en Likert 5 · PLS-SEM (SmartPLS 3.0) + fsQCA 3.0 · aprobación IRB (Jiaxing University).

## Por qué este artículo

Reúne, en un solo caso y de forma bien documentada, **todas** las operaciones que el
doctorando debe aprender a auditar, con matices ricos para comentar en vivo. Además es un
buen puente hacia el banco: usa **fsQCA**, igual que el Art.8 del banco (Mikalef et al., 2019).

## Guion de la demostración (operaciones a modelar en vivo)

El tutor recorre, en este orden, las mismas operaciones de la Plantilla de Análisis
Metodológico (ver [`../plantillas/`](../plantillas/)):

1. **Paradigma epistemológico.** Post-positivista **implícito** — el artículo nunca lo declara. Buen momento para mostrar cómo se *infiere* el paradigma a partir del tipo de hipótesis y del tratamiento de los datos.
2. **Tipo de estudio y diseño.** Observacional, correlacional, transversal, basado en encuesta. Clasificar según el marco de Wohlin et al.
3. **Variables, constructos y operacionalización.** 7 constructos latentes, escala Likert 5. Leer en vivo la fiabilidad y validez: α de Cronbach, CR, AVE, criterio de Fornell-Larcker y HTMT (Tablas 2 y 4 del artículo).
4. **Muestreo y potencia.** n = 225 por bola de nieve (no probabilístico) vía grupos de WeChat. **El artículo no reporta cálculo de potencia a priori** → escenario ideal para ejecutar `statsmodels.stats.power` en vivo y discutir si 225 basta para los efectos detectados.
5. **Amenazas a la validez (4 categorías de Wohlin).**
   - *Interna:* diseño transversal → causalidad limitada.
   - *Externa:* muestra autoseleccionada, sesgada por género (183 M / 42 H) y edad (86% de 18–25), solo China → generalización limitada.
   - *De constructo:* CMB evaluado solo con la prueba de un factor de Harman (defensa débil, criticable).
   - *De conclusión estadística:* tensión entre PLS-SEM (simétrico) y fsQCA (asimétrico); interpretar qué aporta cada uno.
6. **Ética y transparencia.** Declara aprobación **IRB** y consentimiento informado (Jiaxing University); datos como material suplementario (S1, CSV) → buen ejemplo de práctica ética y de datos abiertos que contrastar.
7. **Interpretación estadística.** 9 de 11 hipótesis "confirmadas", con **hipótesis rechazadas** (H2c, H6a, H8a) → enseñar que una hipótesis falsada es un resultado válido, no un fracaso. Discutir qué significa "confirmar" (Wasserstein & Lazar, 2016).
8. **Verificación de potencia en Python.** Cerrar ejecutando la [`potencia_plantilla.ipynb`](../plantillas/potencia_plantilla.ipynb) sobre este artículo, mostrando el flujo completo en un Jupyter Notebook en tiempo real.

## Cómo la usa el estudiante

Quien no pueda asistir en vivo debe **ver la grabación completa** antes de iniciar la Semana 3.
La sesión es el "corazón pedagógico" del ciclo: el estudiante no solo escucha conceptos, sino
que observa el proceso analítico completo antes de replicarlo sobre su propio artículo del
banco.

---

*Referencias del entorno en formato APA 7 en [`../../docs/bibliografia.md`](../../docs/bibliografia.md).*
