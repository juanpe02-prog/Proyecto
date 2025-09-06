# Proyecto
# Simulación FV – Medellín (Python + ERA5)

Proyecto académico para simular un **mes** de producción de un sistema fotovoltaico y comparar contra **datos reales ERA5** (Open-Meteo).  
Incluye: cálculo de posición solar, irradiancia en el plano del panel (POA), potencia (PVWatts), energía diaria, gráficas y presentación.

## Requisitos
- Python 3.9+
- pip (gestor de paquetes)

```bash
pip install pvlib pandas matplotlib requests geopy timezonefinder python-pptx

## Ejecución
```bash
python simulacion_fv.py
## Qué hace
El código sigue este flujo de trabajo:

1. **Entradas del usuario** → ciudad, año, mes, inclinación, azimut y potencia nominal.  
2. **Ubicación** → obtiene latitud, longitud y zona horaria de la ciudad.  
3. **Tiempo del mes** → genera un calendario de todo el mes con intervalos de 30 minutos.  
4. **Posición solar y cielo despejado** → calcula la trayectoria solar y la irradiancia ideal (Ineichen).  
5. **Irradiancia POA** → proyecta la radiación directa, difusa y global al plano inclinado del panel.  
6. **Potencia FV (PVWatts)** → estima la potencia instantánea teniendo en cuenta irradiancia y temperatura de celda.  
7. **Energía diaria** → integra la potencia para obtener energía por día y guarda un CSV con los valores.  
8. **Datos reales ERA5** → descarga radiación y clima del mejor día del mes (GHI, DNI, DHI, temperatura y viento).  
9. **Comparación** → calcula POA y potencia con ERA5 y compara con el modelo de cielo despejado.  
10. **Visualización** → genera las gráficas:  
    - Energía diaria del mes (barras).  
    - Altitud solar del mejor día.  
    - Comparación POA modelo vs ERA5.  
    - Comparación Potencia modelo vs ERA5.  
    - Energía total del mejor día (barras modelo vs real).  
