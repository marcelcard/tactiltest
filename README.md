# Prueba táctil 10×10

Herramienta web (un solo archivo, sin dependencias) para diagnosticar pantallas táctiles, pensada para un monitor Full HD (1920×1080) de 22".

## Uso

- **Local:** abre `index.html` en Chrome o Edge y pulsa `F` para pantalla completa.
- **Online:** súbelo a GitHub y activa *Settings → Pages → Deploy from branch → main / (root)*. Abre la URL que te da GitHub desde el monitor a probar.

> En Windows, pon la escala de pantalla en **100 %** (Configuración → Pantalla). Con otra escala, el navegador reporta menos píxeles de los físicos.

## Modos

| Tecla | Modo | Qué detecta |
|---|---|---|
| `1` | Puntos | Toca los 100 puntos. Verde = respondió. El punto negro es donde el monitor registró el toque, así ves desvíos de calibración. |
| `2` | Líneas | Desliza el dedo sobre las 10 filas, 10 columnas y 2 diagonales. Verde = cubierto, **rojo = tramo sin respuesta** dentro de la línea. Naranja = salto brusco entre muestras. X roja = el toque se cortó (`pointercancel`). |
| `3` | Multitoque | Cuenta toques simultáneos y muestra el máximo alcanzado. |
| `4` | Bordes | 44 puntos sobre el perímetro y las 4 esquinas, donde más fallan los paneles. |

Otras teclas: `R` reinicia, `F` pantalla completa. El botón **Reporte** muestra un resumen y permite descargar un JSON.

## Cómo interpretar

- **Punto que nunca se pone verde:** zona muerta.
- **Tramos rojos en una fila o columna:** fallo en esa línea del sensor (típico de una banda de electrodos defectuosa).
- **Muchos saltos o cortes:** ruido, cable USB/ground deficiente o interferencia. Prueba otro puerto/cable y limpia la pantalla.
- **Desviación > 30 px consistente en una zona:** necesita calibración.
- Desliza despacio en el modo líneas; un deslizamiento muy rápido deja segmentos sin muestras aunque el sensor esté bien.

## Subir a GitHub

```bash
git init
git add index.html README.md
git commit -m "Prueba táctil 10x10"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/touch-test.git
git push -u origin main
```
