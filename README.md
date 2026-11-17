# GP-S · Caso integrador Bebidas del Maipo S.A.

Repositorio del grupo 7 para el caso integrador del curso **Gestión de Producción de Bienes y Servicios** (Universidad de Santiago de Chile). Reúne los datos del caso, el código de cada entrega y los resultados que genera.

## Integrantes

Úrsula Urrutia · Camilo Ascencio · Álvaro Cortés · Juan José Ogaz

Profesores: Luis Rojo · Sebastián Dávila · Cristian Durán

## El caso

**Bebidas del Maipo S.A. (BdM)** es una embotelladora regional con planta en Cerrillos (Región Metropolitana). Produce tres familias de bebidas (néctar de durazno, cítrico de limón y funcional de berries), cada una en tres formatos (0,5, 1,5 y 3,0 L), para un total de 9 SKU activos. Abastece dos centros de distribución propios, dos cadenas de supermercados con contrato de nivel de servicio y un canal mayorista.

El proceso tiene dos etapas en serie: una única mezcladora de jarabe, que es el cuello de botella, y dos líneas de envasado dedicadas por formato (L1 para 0,5 L y L2 para 1,5 y 3,0 L). Entre familias distintas hay limpiezas CIP cuyo tiempo depende de la secuencia.

El caso es un solo proyecto que se construye por capas: lo que se concluye en una entrega es dato de entrada de la siguiente. Los datos vienen de un ERP real y no están limpios, por lo que identificar y tratar sus anomalías es parte del trabajo.

## Entregas

| Entrega | Tema | Estado |
|---|---|---|
| 1 | Calidad y pronóstico | Entregada (21/10/2026); código corregido según la retroalimentación del 04/11/2026 |
| 2 | Planificación de producción e inventario | Pendiente |
| Final | Secuenciamiento e integración | Pendiente |

## Estructura del repositorio

| Ruta | Contenido |
|---|---|
| `datos/` | Datos crudos del caso en CSV (no se modifican; toda transformación ocurre en el código). El diccionario de datos está en la sección 5 del enunciado |
| `Entrega1_BdM_v2.ipynb` | Cuaderno de Colab de la Entrega 1: calidad, limpieza de la demanda, pronóstico y traspasos a la Entrega 2 |
| `Entrega2_BdM.ipynb` | Cuaderno de Colab de la Entrega 2: puente con los traspasos de la E1, modelo de lot-sizing capacitado (§7.1), resolución, verificador independiente, política de referencia, sensibilidad, cuadro de mando (§7.2) y programa congelado de la semana 12 (§7.3) |
| `resultados/` | Salida de la Entrega 1: tablas, figuras y los traspasos `traspaso_C1` a `traspaso_C4b` que lee la Entrega 2 |
| `resultados_E2/` | Salida de la Entrega 2: plan del modelo y de la política de referencia, `corridas_MIP.csv` (semilla, límite de tiempo, estado y brecha de cada corrida del solver), sensibilidad, cuadro de mando, programa de la semana 12 y `config_modelo_E2.json` |
| `requirements.txt` | Versiones fijadas de las librerías (Python 3.13, Google Colab) |
| `Enunciado (1).pdf` | Enunciado del caso |
| `Informe_Entrega1_BdM_Grupo_7.pdf` | Informe de la Entrega 1 |

## Cómo reproducir los resultados

1. Abrir el cuaderno de la entrega en Google Colab (`Entrega1_BdM_v2.ipynb` o `Entrega2_BdM.ipynb`).
2. Ir a **Entorno de ejecución → Desconectar y borrar entorno de ejecución** y luego a **Entorno de ejecución → Ejecutar todo**. Reiniciar no basta: la carpeta `GP-S` de una ejecución anterior queda en la sesión y el cuaderno no vuelve a clonar el repositorio.
3. El cuaderno clona este repositorio, lee los datos de `GP-S/datos` (y, en la Entrega 2, los traspasos de `GP-S/resultados`) y escribe su carpeta de resultados.

Los resultados son deterministas:

- **Entrega 1:** semilla `20260923`. Los parámetros y versiones de la ejecución quedan en `resultados/config_ejecucion.json`.
- **Entrega 2:** solver HiGHS 1.15.1 a través de PuLP 2.9.0, con semilla `2026`, un hilo, tolerancia de brecha de 150.000 CLP y límite de tiempo en cada corrida. Cada corrida queda registrada en `resultados_E2/corridas_MIP.csv`, y la configuración completa (decisiones del modelo, versiones y resultado) en `resultados_E2/config_modelo_E2.json`. El cuaderno tarda alrededor de 20 minutos en Colab, porque resuelve el modelo diez veces (modelo completo, detección del fin de horizonte y ocho escenarios de sensibilidad).

Para ejecutarlo en local:

```bash
git clone https://github.com/camiloascencio-hash/GP-S.git
cd GP-S
pip install -r requirements.txt
```

## Criterios del proyecto

- **Trazabilidad.** Cada cifra, tabla y figura de los informes se puede rastrear hasta un archivo de `resultados/` o `resultados_E2/`.
- **Sin fuga de datos.** Los datos de prueba no se usan para ajustar ni para elegir modelos.
- **Verificación independiente.** En la Entrega 2, cada plan se recalcula desde cero, sin el solver, y se comprueban todas sus restricciones antes de usarlo.

## Uso de Inteligencia Artificial

Se usó IA como apoyo en redacción, formato y estructura del código. La lógica y las conclusiones son del grupo. El detalle está en la declaración de cada informe.
