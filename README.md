# Primer Parcial de Ciencias de Datos

**Fecha de entrega:** 10 de Junio de 2026

## Entregables

- Jupyter Notebook
- Predicciones sobre el dataset `bank_product_propensity_predict.csv`

## Resumen

- Entrenar y validar el modelo utilizando el set de datos `bank_product_propensity_dataset.csv`.
- Aplicar el modelo entrenado para predecir la probabilidad de adquisición del producto en los clientes incluidos en el set de datos `bank_product_propensity_predict.csv`. Entregar el resultado en CSV junto con el notebook.

---

## Introducción

Estás trabajando como Científico de IA para un banco minorista. El equipo de marketing quiere identificar clientes que tienen mayor probabilidad de adquirir un nuevo producto de **inversión** premium. Tu tarea es construir un modelo predictivo que pueda identificar con precisión clientes de alta propensión, permitiendo al equipo de marketing dirigir sus campañas de manera más efectiva y mejorar las tasas de conversión.

El producto de inversión premium requiere:

- Saldos mínimos en cuentas
- Engagement bancario activo
- Estabilidad financiera
- Interés en inversiones

---

## Descripción del Dataset

### Granularidad

- **Nivel:** Snapshot Cliente-Mes
- **Estructura:** Cada fila representa un cliente en un mes específico
- **Tamaño:** ~48,000 filas (10,000 clientes × 6 meses)
- **Variables:** 64 variables + 1 variable objetivo

### Variable Objetivo

- **Nombre:** `target_product_acquired`
- **Tipo:** Clasificación binaria (0 = no adquirió, 1 = adquirió)

### Archivos Proporcionados

1. `bank_product_propensity_dataset.csv` — Dataset para training y testing
2. `bank_product_propensity_predict.csv` — Dataset de aplicación y entregable

### Resultados Baseline

AUC-ROC ~0.70 (intencionalmente subóptimo)

---

## Entregables del Parcial

### Jupyter Notebook que incluya

#### 1. Exploración de Datos (Breve)

- Resumen del dataset
- Análisis de valores faltantes
- Análisis de distribución del objetivo
- Insights clave

#### 2. Ingeniería de Variables

- Nuevas variables creadas con explicaciones
- Análisis de importancia de variables
- Comparación de rendimiento del modelo con/sin nuevas variables
- Limpieza de datos

#### 3. Modelo Final

- Mejor modelo con todas las mejoras
- Métricas de evaluación comprehensivas
- Visualización de importancia de variables
- Recomendaciones de negocio

#### 4. Resumen

- Tabla de comparación de rendimiento (baseline vs. final)
- Insights clave y recomendaciones
- Próximos pasos para mejora adicional

### Predict CSV

- Debe incluir las predicciones sobre cada cliente del set de datos `bank_product_propensity_predict.csv`.

---

## Métricas de Éxito

### Requisitos Mínimos para Aprobar

- **AUC-ROC:** ≥ 0.70 (vs. baseline ~0.65–0.70)

### Rendimiento Excelente

- **AUC-ROC:** ≥ 0.80

---

> **Nota:** Este es un escenario ficticio con datos sintéticos. No se utilizan datos reales de clientes.

---

## Catálogo del Dataset — Propensión a Productos Bancarios

### Descripción General

Este dataset contiene instantáneas de clientes a intervalos mensuales, rastreando el comportamiento y características bancarias para predecir la propensión a adquirir un producto de inversión premium.

- **Granularidad:** Nivel Cliente-Mes (cada fila representa un cliente en un mes específico)
- **Variable Objetivo:** `target_product_acquired` (1 = adquirió el producto, 0 = no adquirió)

### Variables de Identificación y Temporales

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `customer_id` | Entero | Identificador único del cliente |
| `snapshot_date` | Fecha | Fecha de fin de mes de la instantánea |

### Variables Demográficas

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `age` | Entero | Edad del cliente en años |
| `employment_status` | Categórica | Tipo de empleo: employed (empleado), self_employed (autónomo), unemployed (desempleado), retired (jubilado) |
| `education_level` | Categórica | Nivel educativo más alto: high_school (secundaria), bachelor (licenciatura), master (maestría), phd (doctorado) |
| `marital_status` | Categórica | Estado civil: single (soltero), married (casado), divorced (divorciado), widowed (viudo) |
| `num_dependents` | Entero | Número de dependientes financieros |
| `owns_home` | Binaria | Propiedad de vivienda (1 = propietario, 0 = inquilino) |

### Variables de Perfil Financiero

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `income` | Float | Ingreso anual en dólares |
| `credit_score` | Float | Puntaje crediticio (300–850) |
| `tenure_months` | Entero | Meses como cliente del banco |
| `num_products` | Entero | Número actual de productos bancarios que posee |

### Variables de Tenencia de Cuentas

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `has_savings_account` | Binaria | Tiene cuenta de ahorros (1 = sí, 0 = no) |
| `has_checking_account` | Binaria | Tiene cuenta corriente (1 = sí, 0 = no) |
| `has_credit_card` | Binaria | Tiene tarjeta de crédito (1 = sí, 0 = no) |
| `has_mortgage` | Binaria | Tiene hipoteca (1 = sí, 0 = no) |
| `has_personal_loan` | Binaria | Tiene préstamo personal (1 = sí, 0 = no) |
| `has_investment_account` | Binaria | Tiene cuenta de inversión (1 = sí, 0 = no) |

### Variables de Saldos de Cuentas

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `savings_balance` | Float | Saldo actual de la cuenta de ahorros |
| `checking_balance` | Float | Saldo actual de la cuenta corriente |
| `credit_card_balance` | Float | Saldo actual de la tarjeta de crédito |
| `investment_balance` | Float | Saldo actual de la cuenta de inversión |
| `avg_monthly_balance` | Float | Promedio de saldos de ahorros + corriente |

### Variables de Actividad Transaccional (Último Mes)

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `num_transactions_last_month` | Entero | Número total de transacciones |
| `num_atm_withdrawals_last_month` | Entero | Número de retiros en cajeros automáticos |
| `num_online_transactions_last_month` | Entero | Número de transacciones en línea |
| `num_pos_transactions_last_month` | Entero | Número de transacciones en punto de venta |
| `total_transaction_amount_last_month` | Float | Volumen total de transacciones |
| `avg_transaction_amount_last_month` | Float | Tamaño promedio de transacción |
| `num_deposits_last_month` | Entero | Número de depósitos |
| `total_deposit_amount_last_month` | Float | Monto total de depósitos |
| `num_withdrawals_last_month` | Entero | Número de retiros |
| `total_withdrawal_amount_last_month` | Float | Monto total de retiros |
| `num_bill_payments_last_month` | Entero | Número de pagos de facturas |
| `total_bill_payment_amount_last_month` | Float | Monto total de pagos de facturas |
| `num_international_transactions_last_month` | Entero | Número de transacciones internacionales |
| `total_international_amount_last_month` | Float | Monto total de transacciones internacionales |

### Variables de Engagement del Cliente

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `num_customer_service_calls_last_month` | Entero | Interacciones con servicio al cliente |
| `num_branch_visits_last_month` | Entero | Visitas a sucursales físicas |
| `num_mobile_logins_last_month` | Entero | Inicios de sesión en app móvil |
| `num_web_logins_last_month` | Entero | Inicios de sesión en portal web |
| `email_open_rate_last_3_months` | Float | Tasa de apertura de emails (0–1) |
| `email_click_rate_last_3_months` | Float | Tasa de clics en emails (0–1) |
| `sms_response_rate_last_3_months` | Float | Tasa de respuesta a SMS (0–1) |

### Indicadores de Salud Financiera

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `credit_utilization_ratio` | Float | Saldo de tarjeta de crédito / crédito disponible |
| `debt_to_income_ratio` | Float | Deuda total / ingreso |
| `num_overdrafts_last_year` | Entero | Número de sobregiros |
| `total_overdraft_fees_last_year` | Float | Total de comisiones por sobregiro pagadas |
| `num_late_payments_last_year` | Entero | Número de pagos atrasados |
| `num_failed_transactions_last_month` | Entero | Intentos de transacciones fallidas |
| `balance_volatility` | Float | Desviación estándar de cambios en saldo |
| `savings_growth_rate_last_6_months` | Float | Tasa de crecimiento del saldo de ahorros |

### Variables de Comportamiento Bancario

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `months_since_last_product_purchase` | Entero | Meses desde la última adquisición de producto |
| `num_products_purchased_last_year` | Entero | Productos adquiridos en los últimos 12 meses |
| `has_direct_deposit` | Binaria | Tiene depósito directo configurado (1 = sí, 0 = no) |
| `has_auto_pay_setup` | Binaria | Tiene pagos automáticos (1 = sí, 0 = no) |

### Variables de Scores Derivados

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `cross_sell_score` | Float | Score propietario de venta cruzada (0–100) |
| `risk_score` | Float | Score de riesgo del cliente (0–100) |
| `customer_lifetime_value` | Float | Valor de vida del cliente estimado en dólares |
| `recency_score` | Float | Componente de recencia RFM (0–100) |
| `frequency_score` | Float | Componente de frecuencia RFM (0–100) |
| `monetary_score` | Float | Componente monetario RFM (0–100) |

---

## Oportunidades Clave de Ingeniería de Variables

1. **Variables de ratio**
2. **Patrones de valores faltantes**
3. **Desbalance de clases**

---

## Variable Objetivo

**`target_product_acquired`**

- **Tipo:** Binaria (0 o 1)
- **Definición:** Si el cliente adquirió el producto en ese mes

---

## Evaluación del Modelo

Usar métricas apropiadas (AUC-ROC, Precision-Recall, F1).

---

## Estructura del Repositorio

| Archivo | Descripción |
|---------|-------------|
| `Parcial.ipynb` | Notebook con el desarrollo del modelo |
| `bank_product_propensity_predictions.csv` | Predicciones generadas sobre el dataset de aplicación |
| `bank_product_propensity_dataset.csv` | Dataset de entrenamiento (provisto por la cátedra) |
| `bank_product_propensity_predict.csv` | Dataset para predecir (provisto por la cátedra) |

## Cómo ejecutar

1. Instalar dependencias:

   ```bash
   pip install -r requirements.txt
   ```

2. Colocar los archivos `bank_product_propensity_dataset.csv` y `bank_product_propensity_predict.csv` en la carpeta del proyecto.

3. Abrir `Parcial.ipynb` y ejecutar todas las celdas (**Run All**), en orden de arriba hacia abajo.

4. Verificar que se genere `bank_product_propensity_predictions.csv` con las columnas `customer_id`, `predicted_probability` y `predicted_class`.
