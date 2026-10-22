# UT1: Primer prototipo de sistema ciberfísico (CPS) para la Industria 4.0
**Módulo:** Digitalización aplicada II (2º DAW)  
**Asignación:** Pareja 2  
**Integrantes:** Ángel Hernández Alonso y Matias
**Correo institucional:** matiasd.ramcha@educa.jcyl.es | angel.heralo.2  

---

## 1. Justificación de la PYME Cliente y Proceso OT
* **Empresa / Entorno cliente:** Centro de Datos (CPD) / Data Center[cite: 2]
* **Ubicación:** Valladolid / León (Castilla y León)[cite: 2]
* **Proceso OT a digitalizar:** Monitorización ambiental continua para la refrigeración de *racks* de servidores y control de seguridad física en sala[cite: 2].
* **Problema operativo y pérdida económica:**  
  * **Temperatura:** Un sobrecalentamiento no detectado en las filas de servidores (*racks*) reduce el rendimiento de los procesadores (*thermal throttling*) y acelera la degradación del *hardware*, pudiendo causar paradas no planificadas de servicios críticos.
  * **Nivel de luz:** La alteración del nivel de luz ambiental permite detectar accesos no autorizados o aperturas prolongadas de las puertas de los *racks* o de la sala blanca, lo que supone un fallo de seguridad física en la infraestructura.

---

## 2. Indicadores Clave de Rendimiento (KPIs)

| KPI | Descripción | Meta / Tolerancia |
| :--- | :--- | :--- |
| **KPI 1: Latencia de captura** | Tiempo transcurrido entre la lectura de los sensores físicos (CPU y luz) y la recepción de datos. | **< 2 segundos** |
| **KPI 2: Precisión y Tolerancia** | Umbral crítico de temperatura ambiente en el *rack* antes de activar la alarma de planta. | **Rango seguro: < 25 °C** (Alerta si $T > 25^\circ\text{C}$) |
| **KPI 3: Estabilidad del sistema** | Porcentaje de tramas clave-valor transmitidas con éxito por el conector USB/Serie. | **100% sin pérdida de tramas** |

---

## 3. Clasificación e Integración IT / OT

| Entorno | Componente / Elemento | Función en el Sistema |
| :--- | :--- | :--- |
| **OT (Operational Technology)** | BBC Micro:bit v2 (Sensores e Indicadores) | Captura de la temperatura de la CPU del procesador de la placa y nivel de radiación lumínica en matriz LED[cite: 2]. Emisión de alertas acústicas y visuales en sala de servidores. |
| **Interfaz / Canal** | Conector MicroUSB / Serie (UART) | Transferencia continua de datos mediante tramas con formato estructurado `clave:valor` enviadas a intervalos de 2000 ms. |
| **IT (Information Technology)** | Sistema de Incidencias de TI y Web Corporativa[cite: 2] | Integración con el sistema de tickets/incidencias de TI para registrar eventos críticos[cite: 2], almacenar el histórico y visualizar métricas de rendimiento corporativo. |

---

## 4. Archivos adjuntos en este directorio
* `microbit-monitor.hex`: Programa compilado desarrollado en MakeCode con la lógica de control del CPD.
* `carcasa-microbit.stl`: Modelo 3D de la carcasa protectora industrial diseñada en Tinkercad con ranuras de convección térmica, espacio para puerto MicroUSB y ventana frontal.
