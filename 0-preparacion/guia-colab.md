# Uso de Google Colab (alternativa sin instalación local)

**Semana 0 · Preparación del entorno técnico · sin puntaje**

**Google Colab** ejecuta notebooks de Jupyter en la nube, sin instalar nada en tu equipo.
Es la alternativa recomendada si tienes poco espacio en disco, problemas de instalación con
Anaconda, o quieres empezar de inmediato. Solo necesitas una **cuenta de Google** y un
navegador.

> ¿Prefieres trabajar localmente? Usa [`instalacion-anaconda.md`](instalacion-anaconda.md).

---

## Ventajas y límites

**A favor:** cero instalación; trae casi todos los paquetes del entorno preinstalados;
accesible desde cualquier equipo.

**Ten en cuenta:** requiere conexión a internet; las sesiones se **reinician** tras un
tiempo de inactividad (pierdes las variables en memoria y los paquetes instalados con `pip`,
por lo que hay que reejecutar); los archivos subidos a la sesión son temporales — guarda tu
trabajo en Google Drive o descárgalo.

---

## Paso 1 · Abrir el notebook de verificación en Colab

Tienes tres formas; usa la que te resulte más cómoda:

- **Subir el archivo:** entra a <https://colab.research.google.com>, pestaña **Subir /
  Upload**, y carga `entorno_verificacion.ipynb` (de la carpeta `0-preparacion/` del
  repositorio).
- **Desde GitHub:** en Colab, menú **Archivo → Abrir cuaderno → GitHub**, pega la URL del
  repositorio y selecciona el notebook.
- **Desde Google Drive:** sube el `.ipynb` a tu Drive y ábrelo con clic derecho → **Abrir con
  → Google Colaboratory**.

---

## Paso 2 · Instalar el paquete que falta (`pingouin`)

Colab **ya trae** pandas, numpy, scipy, statsmodels, scikit-learn, matplotlib y seaborn.
Solo falta `pingouin` (Ciclo 2, Semana 6). En la **primera celda** del notebook, ejecuta:

```python
!pip install pingouin
```

Luego reinicia el entorno para que el paquete quede disponible:
menú **Entorno de ejecución → Reiniciar sesión** (*Runtime → Restart session*).

> **Importante:** cada vez que Colab reinicia la sesión debes volver a ejecutar
> `!pip install pingouin`. Colab no conserva las instalaciones entre sesiones.

---

## Paso 3 · Ejecutar la verificación completa

1. Menú **Entorno de ejecución → Ejecutar todas** (*Runtime → Run all*).
2. Baja hasta la celda final y confirma que el informe diga ✅ **ENTORNO LISTO**.
3. Toma una **captura de pantalla** de esa celda y consérvala (puede solicitarse como evidencia).

Si alguna celda de paquete muestra ❌, revisa que hayas ejecutado el `!pip install pingouin`
y reiniciado la sesión antes de "Ejecutar todas".

---

## Paso 4 · Guardar tu trabajo

Los notebooks de Colab **no se guardan solos** en tu repositorio. Al terminar:

- **En Drive:** menú **Archivo → Guardar una copia en Drive**.
- **Descargar el `.ipynb`:** menú **Archivo → Descargar → Descargar .ipynb** para adjuntarlo
  a tus entregas y subirlo al repositorio.

Para los ciclos siguientes, sube el **dataset** de la cohorte a la sesión con el panel
**Archivos** (icono de carpeta a la izquierda) o móntalo desde Drive:

```python
from google.colab import drive
drive.mount('/content/drive')
```

---

## Consideración sobre reproducibilidad (FAIR)

El entorno exige que tus notebooks sean **reproducibles de principio a fin**. En Colab, antes
de una entrega:

1. Menú **Entorno de ejecución → Reiniciar y ejecutar todo** (*Restart and run all*): debe
   correr sin errores desde cero.
2. Incluye al inicio la celda `!pip install ...` con las librerías que uses, para que
   cualquiera pueda reproducir tu análisis.
3. Fija las versiones cuando sea posible; puedes listarlas con:
   ```python
   !pip freeze > requirements-colab.txt
   ```

---

## Solución de problemas

| Síntoma | Qué hacer |
|---|---|
| `ModuleNotFoundError: pingouin` tras un rato | La sesión se reinició. Vuelve a ejecutar `!pip install pingouin` y reinicia la sesión. |
| El notebook "olvidó" mis variables | Colab cerró la sesión por inactividad. Usa **Ejecutar todas** para reconstruir el estado. |
| Perdí un archivo que había subido | Los archivos de la sesión son temporales. Guárdalos en Drive o vuelve a subirlos. |
| Necesito una librería avanzada del Ciclo 2 (PyMC, semopy, arviz, mlxtend) | Instálala con `!pip install <paquete>` al inicio del notebook de ese ciclo. |
| La sesión va lenta | En **Entorno de ejecución → Cambiar tipo de entorno** puedes elegir acelerador; para este curso la CPU estándar basta. |

---

## ¿Sigues con problemas?

Comunícalo al docente **por el correo del campus virtual antes del inicio de la Semana 1**,
indicando el paso en el que falló y el mensaje de error exacto (una captura ayuda). Resolverlo
a tiempo garantiza que la Semana 1 se dedique íntegramente a los contenidos metodológicos.
