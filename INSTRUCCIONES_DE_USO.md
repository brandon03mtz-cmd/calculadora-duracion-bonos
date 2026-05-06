# Calculadora de Duración, Modified Duration y Aproximación de Cambios en Precios de Bonos

## 📋 Descripción

Esta calculadora Excel permite calcular:
- **Precio del bono** con tasa de rendimiento inicial (i)
- **Precio del bono** con tasa de rendimiento modificada (i + h)
- **Duración (Duration)** del bono
- **Modified Duration (MD)** del bono
- **Aproximación de primer orden** del cambio en el precio ante cambios en tasas

## 🎯 Parámetros Requeridos

| Parámetro | Descripción | Ejemplo |
|-----------|-------------|---------|
| **Valor Nominal (VN)** | Valor facial del bono | 1,000 |
| **Tasa Cupón (c)** | Tasa de cupón anual | 5% |
| **Rendimiento Inicial (i)** | Tasa de rendimiento (yield) inicial | 4% |
| **Cambio de Tasa (h)** | Cambio en la tasa de rendimiento | 1% ó -1% |
| **Plazo (n)** | Años hasta vencimiento | 5 |
| **Frecuencia de Cupones** | Pagos anuales (1) o semestrales (2) | 1 ó 2 |

## 📐 Fórmulas Utilizadas

### 1. Precio del Bono
```
P = Σ [C / (1 + y)^t] + [VN / (1 + y)^n]

Donde:
- C = Cupón periódico
- y = Rendimiento periódico
- t = Período
- VN = Valor nominal
```

### 2. Duración (Duration de Macaulay)
```
D = Σ [t × (CF_t / (1 + y)^t)] / P

Donde:
- CF_t = Flujo de caja en período t
- P = Precio actual del bono
```

### 3. Modified Duration
```
MD = D / (1 + y)
```

### 4. Aproximación de Primer Orden (ΔP)
```
ΔP ≈ -MD × P × Δy

Donde:
- Δy = Cambio en el rendimiento (h)
```

## 📊 Ejemplo Práctico Completo

### Datos del Bono:
- **Valor Nominal:** $1,000
- **Tasa de Cupón:** 5% anual
- **Rendimiento Inicial (i):** 4% anual
- **Cambio de Tasa (h):** +1% (de 4% a 5%)
- **Plazo:** 5 años
- **Frecuencia:** Anual (1 pago por año)

### Resultados Esperados:

| Métrica | Valor |
|---------|-------|
| **Precio con i = 4%** | $1,082.27 |
| **Precio con i + h = 5%** | $1,000.00 |
| **Duración** | 4.54 años |
| **Modified Duration** | 4.37 |
| **Cambio Real de Precio (ΔP Real)** | -$82.27 |
| **Cambio Estimado (1er Orden)** | -$47.26 |
| **Error de Aproximación** | $35.01 |

### Interpretación:
- Si el rendimiento **sube 1%** (de 4% a 5%), el precio del bono **cae aproximadamente $47.26** según la aproximación de primer orden
- El cambio real es de -$82.27 (la diferencia se debe a la convexidad)
- La Modified Duration de 4.37 significa que por cada cambio de 1% en la tasa, el precio cambia aproximadamente 4.37%

## 🖥️ Cómo Usar la Calculadora

### Paso 1: Abre el archivo Excel
Descarga y abre `Calculadora_Duracion_Bonos.xlsx`

### Paso 2: Ingresa los parámetros en la sección "ENTRADA DE DATOS"
- **Celda B2:** Valor Nominal del bono (ej: 1000)
- **Celda B3:** Tasa de Cupón anual en % (ej: 5)
- **Celda B4:** Rendimiento Inicial - i en % (ej: 4)
- **Celda B5:** Cambio de Tasa - h en % (ej: 1 o -1)
- **Celda B6:** Plazo en años (ej: 5)
- **Celda B7:** Frecuencia de cupones: 1 para anual, 2 para semestral

### Paso 3: Observa los resultados en la sección "RESULTADOS"
La calculadora mostrará automáticamente:
- Precio con tasa i
- Precio con tasa i + h
- Duration (Duración de Macaulay)
- Modified Duration
- Cambio en precio real vs estimado

### Paso 4: Analiza la tabla de flujos de caja
Visualiza el desglose período por período de:
- Flujos de caja
- Factores de descuento
- Valor presente de cada flujo

## ⚠️ Notas Importantes

✓ Los porcentajes pueden ingresarse como números normales (5 para 5%) o decimales (0.05)
✓ La calculadora soporta bonos con cupones anuales o semestrales
✓ La aproximación de primer orden es más precisa para cambios pequeños en tasas (< 2%)
✓ Para cambios grandes, la diferencia entre valor estimado y real refleja el efecto de convexidad
✓ Todos los cálculos se actualizan automáticamente al cambiar un parámetro

## 📝 Ejemplo de Uso Paso a Paso

**Escenario:** Analizar un bono corporativo de IBM

1. Abre el Excel
2. Ingresa en la sección ENTRADA DE DATOS:
   - VN = 1000
   - Cupón = 5
   - Rendimiento = 4
   - Cambio = 1
   - Plazo = 5
   - Frecuencia = 1

3. **Resultados automáticos:**
   - Verás el precio actual ($1,082.27), la duración (4.54 años)
   - La Modified Duration (4.37) te indica que si suben las tasas 1%, el precio caerá ~4.37%
   - La aproximación de primer orden estima una caída de $47.26
   - El cambio real es -$82.27 (incluye el efecto de convexidad)

4. **Usa estos datos para:**
   - Evaluar el riesgo de tasa de interés
   - Comparar bonos con diferentes duraciones
   - Tomar decisiones sobre posiciones de renta fija

## 🔄 Ejemplo con Cambio Negativo

Si cambias h de +1 a -1 (tasas bajan):

| Métrica | Valor |
|---------|-------|
| **Precio con i = 4%** | $1,082.27 |
| **Precio con i - 1% = 3%** | $1,169.86 |
| **Cambio Estimado (1er Orden)** | +$47.26 |
| **Cambio Real** | +$87.59 |

La relación es inversa: si las tasas bajan, el precio del bono sube.

---

**Creado por:** brandon03mtz-cmd
**Fecha:** 2026-05-06
**Contacto:** GitHub @brandon03mtz-cmd
