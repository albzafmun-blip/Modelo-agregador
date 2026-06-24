# Apéndice B: Modelo de Optimización (Pyomo) y Visualización

**Trabajo Fin de Grado:** Análisis tecno-económico del modelo de negocio del agregador en España  
**Autor:** Alberto Zafra Muñoz | Universidad de Sevilla (2026)  

Este repositorio contiene el código fuente principal desarrollado para el Trabajo de Fin de Grado. El *script* unifica tanto el **motor de cálculo matemático** (resolución del problema de optimización) como el **motor de visualización** (generación de las gráficas analíticas presentes en la memoria).

---

## ⚙️ Descripción del Código

El archivo principal (`modelo_agregador.py`) implementa un modelo de Programación Lineal Entera Mixta (MILP) que simula el comportamiento de un Agregador Independiente gestionando un clúster de Recursos Energéticos Distribuidos (DERs). 

El *script* realiza las siguientes operaciones en una única ejecución:
1. **Ingesta de datos:** Carga de las series temporales normalizadas (demanda, generación y precios de mercado).
2. **Construcción del modelo algebraico:** Declaración de variables, restricciones físicas (baterías, cargas, inversores) y balances económicos (mecanismo *Shared Savings*).
3. **Optimización:** Llamada al *solver* para encontrar el óptimo global operativo.
4. **Análisis de Sensibilidad:** Ejecución de una rutina iterativa que evalúa el modelo bajo diferentes escenarios de activación estocástica del mercado aFRR y distintos esquemas de precios de flexibilidad.
5. **Generación de Resultados Visuales:** Representación gráfica automática de los resultados. Este código es el responsable directo de generar las **Figuras 4.6, 4.7, 4.8 y 4.9** incluidas en el documento final.

---

## 🛠️ Requisitos Previos y Entorno

Para ejecutar el código correctamente, es necesario disponer de un entorno de Python (versión 3.8 o superior) con los siguientes paquetes instalados:

* `pyomo` (Modelado matemático)
* `pandas` (Gestión de bases de datos y series temporales)
* `matplotlib` (Generación de gráficos)

Adicionalmente, el modelo requiere el motor de resolución comercial **Gurobi** (`gurobipy`). Asegúrese de contar con una licencia válida (académica o comercial) instalada y configurada en las variables de entorno de su sistema operativo.

---

## 🚀 Instrucciones de Uso

1. **Descarga de Datos:** El modelo requiere alimentarse de los datos de mercado y perfiles físicos correspondientes a la jornada de estudio. Estos archivos `.csv` se encuentran alojados de forma independiente en el repositorio del **Apéndice A**.
2. **Ubicación de Archivos:** Descargue los archivos `.csv` con sufijo `_Limpios` y colóquelos en el mismo directorio raíz donde se encuentre el *script* `modelo_agregador.py`.
3. **Ejecución:** Lance el *script* desde su terminal o IDE preferido:
```bash
   python modelo_agregador.py
