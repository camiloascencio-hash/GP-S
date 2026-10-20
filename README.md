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
| 1 | Calidad y pronóstico | Entregada |
| 2 | Planificación de producción e inventario | Pendiente |
| Final | Secuenciamiento e integración | Pendiente |

## Estructura del repositorio

| Ruta | Contenido |
|---|---|
| `datos/` | Datos del caso en CSV y su descripción |
| Cuadernos | Un cuaderno de Colab por entrega, con el código y su explicación |
| `resultados/` | Tablas, figuras y archivos que genera el código, usados en los informes |
| `requirements.txt` | Versiones de las librerías |

## Cómo reproducir los resultados

1. Abrir el cuaderno de la entrega en Google Colab.
2. Ir a **Entorno de ejecución → Reiniciar y ejecutar todo**.
3. El cuaderno clona este repositorio, lee los datos de `GP-S/datos` y escribe la carpeta `resultados/`.

Los resultados son deterministas (semilla `20260923`). Los parámetros y versiones de cada ejecución quedan en `resultados/config_ejecucion.json`.

Para ejecutarlo en local:

```bash
git clone https://github.com/camiloascencio-hash/GP-S.git
cd GP-S
pip install -r requirements.txt
```

## Criterios del proyecto

- **Trazabilidad.** Cada cifra, tabla y figura de los informes se puede rastrear hasta un archivo de `resultados/`.
- **Sin fuga de datos.** Los datos de prueba no se usan para ajustar ni para elegir modelos.

## Uso de Inteligencia Artificial

Se usó IA como apoyo en redacción, formato y estructura del código. La lógica y las conclusiones son del grupo. El detalle está en la declaración de cada informe.
