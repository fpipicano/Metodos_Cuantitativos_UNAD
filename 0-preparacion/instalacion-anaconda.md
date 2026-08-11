# Instalación de Anaconda

**Semana 0 · Preparación del entorno técnico · sin puntaje**

Esta guía te lleva paso a paso a instalar **Anaconda** y dejar tu entorno Python/Jupyter
listo **antes de la Semana 1** del Ciclo 1. Anaconda incluye Python y casi todos los paquetes
del entorno en una sola instalación.

> ¿Prefieres no instalar nada localmente? Usa la alternativa en la nube:
> [`guia-colab.md`](guia-colab.md).

---

## Antes de empezar

- **Espacio en disco:** ~5 GB libres.
- **Permisos:** una cuenta de usuario normal es suficiente; **no** instales "para todos los usuarios" salvo que sepas por qué.
- **Conexión estable:** el instalador pesa alrededor de 1 GB.

---

## Paso 1 · Descargar el instalador

1. Entra a la página oficial de descargas: <https://www.anaconda.com/download>.
2. Puede pedirte un correo; existe también un enlace de descarga directa sin registro en esa misma página.
3. Elige el instalador de **tu sistema operativo** (Windows, macOS o Linux) y, en macOS, el que corresponda a tu procesador (**Apple Silicon** M1/M2/M3… o **Intel**).

> Alternativa ligera: si tienes poco espacio, puedes instalar **Miniconda**
> (<https://docs.conda.io/en/latest/miniconda.html>) y luego crear el entorno con el
> `environment.yml` del repositorio. Anaconda es más simple para empezar; Miniconda es más
> liviano.

---

## Paso 2 · Instalar

### Windows

1. Ejecuta el archivo `.exe` descargado.
2. Acepta la licencia y elige **"Just Me" (recomendado)**.
3. Deja la ruta de instalación por defecto.
4. En "Advanced Options", **deja desmarcada** la opción de agregar Anaconda al `PATH` (usarás el *Anaconda Prompt*, que ya lo configura).
5. Finaliza la instalación.

### macOS

1. Abre el archivo `.pkg` descargado y sigue el asistente gráfico.
2. Instala **"para mí solamente" (Install for me only)**.
3. Al terminar, abre la app **Terminal** para las verificaciones del Paso 3.

### Linux

1. Abre una terminal en la carpeta de descargas y da permisos de ejecución:
   ```bash
   bash Anaconda3-*-Linux-x86_64.sh
   ```
2. Acepta la licencia (`yes`), confirma la ruta por defecto y, al preguntar por `conda init`, responde **`yes`**.
3. Cierra y vuelve a abrir la terminal para que los cambios tomen efecto.

---

## Paso 3 · Verificar la instalación

Abre el **Anaconda Prompt** (Windows) o la **Terminal** (macOS/Linux) y ejecuta:

```bash
conda --version
python --version
```

Deberías ver la versión de conda y **Python 3.9 o superior**. Si ambos comandos responden,
la instalación fue correcta.

---

## Paso 4 · Instalar el paquete que falta (`pingouin`)

Anaconda trae pandas, numpy, scipy, statsmodels, scikit-learn, matplotlib y seaborn, pero
**no** incluye `pingouin` (se usa en el Ciclo 2, Semana 6). Instálalo con:

```bash
pip install pingouin
```

> Opción recomendada — entorno reproducible: en lugar de instalar paquetes sueltos, crea el
> entorno exacto del curso desde la raíz del repositorio:
> ```bash
> conda env create -f environment.yml
> conda activate metodos-cuantitativos-dti
> ```
> Así fijas las mismas dependencias para toda la cohorte (buena práctica FAIR).

---

## Paso 5 · Abrir Jupyter y ejecutar la verificación

1. Abre **Anaconda Navigator** (interfaz gráfica) y lanza **JupyterLab** o **Jupyter Notebook**; o hazlo por terminal:
   ```bash
   jupyter lab
   ```
2. Navega hasta la carpeta `0-preparacion/` del repositorio y abre **`entorno_verificacion.ipynb`**.
3. Ejecuta todo el notebook: menú **Kernel → Restart Kernel and Run All Cells**.
4. Baja hasta la celda final y confirma que el informe diga ✅ **ENTORNO LISTO**.
5. Toma una **captura de pantalla** de esa celda y consérvala (puede solicitarse como evidencia).

---

## Solución de problemas

| Síntoma | Qué hacer |
|---|---|
| `conda: command not found` (o no reconocido) | En Windows, usa el **Anaconda Prompt**, no la consola normal. En macOS/Linux, cierra y reabre la terminal, o ejecuta `conda init` y reiníciala. |
| `pip` instala pero el paquete "no aparece" en Jupyter | Verifica que Jupyter usa el kernel de Anaconda: en el notebook, `import sys; print(sys.executable)` debe apuntar a la ruta de Anaconda. |
| `ModuleNotFoundError: pingouin` | Ejecuta `pip install pingouin` en el **mismo** entorno donde corres Jupyter y reinicia el kernel. |
| La instalación se queda "colgada" resolviendo el entorno | Usa `conda env create -f environment.yml` (más rápido y determinista) o instala Miniconda. |
| Choque de versiones entre paquetes | Crea un entorno limpio: `conda create -n mcdti python=3.11` y luego instala desde `requirements.txt`. |

---

## ¿Sigues con problemas?

Comunícalo al docente **por el correo del campus virtual antes del inicio de la Semana 1**,
indicando:

- tu **sistema operativo** y versión,
- el **paso** en el que falló,
- el **mensaje de error exacto** (una captura de pantalla ayuda).

Resolverlo a tiempo garantiza que la Semana 1 se dedique íntegramente a los contenidos
metodológicos.
