# 0 · Preparación del entorno técnico

**Semana 0 · Actividad previa · sin puntaje**

Configura tu entorno de trabajo **Python / Jupyter antes de que inicie el Ciclo 1**, para
que la Semana 1 se dedique íntegramente a los contenidos metodológicos.

## Pasos

1. **Prepara Python.** Elige una de las dos vías:
   - **Instalación local con Anaconda** — sigue [`instalacion-anaconda.md`](instalacion-anaconda.md). Anaconda incluye los paquetes base del entorno (pandas, scipy, statsmodels, scikit-learn, matplotlib, seaborn); `pingouin` se instala aparte con `pip install pingouin`.
   - **Sin instalar nada (en la nube)** — sigue [`guia-colab.md`](guia-colab.md) para trabajar en Google Colab.
2. **Ejecuta** [`entorno_verificacion.ipynb`](entorno_verificacion.ipynb) completo (Kernel → *Restart & Run All*). Comprueba que cada paquete carga en una versión compatible.
3. **Verifica** que la celda final muestre ✅ **ENTORNO LISTO** y guarda una captura de pantalla (puede solicitarse como evidencia).

Si algún paquete falla, comunícalo al docente por el correo del campus virtual **antes** del
inicio de la Semana 1, indicando el sistema operativo y el mensaje de error exacto.

## Contenido

| Archivo | Qué es |
|---|---|
| [`entorno_verificacion.ipynb`](entorno_verificacion.ipynb) | Notebook que verifica versiones de todos los paquetes y ejecuta una prueba funcional integrada. Se entrega reejecutado como referencia (salida ✅). |
| [`instalacion-anaconda.md`](instalacion-anaconda.md) | Guía paso a paso de instalación de Anaconda. |
| [`guia-colab.md`](guia-colab.md) | Uso de Google Colab como alternativa sin instalación local. |

> Las dependencias completas del entorno están en [`requirements.txt`](../requirements.txt)
> y [`environment.yml`](../environment.yml), en la raíz del repositorio.
