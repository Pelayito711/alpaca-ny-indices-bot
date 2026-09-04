# Bot de Trading Auto-Correctivo para Índices de Nueva York (QQQ & SPY)

Bot autónomo de trading cuantitativo para operar el mercado de **Nueva York (09:30 - 16:00 EST)** en los índices bursátiles **Nasdaq 100 (`QQQ`)** y **S&P 500 (`SPY`)** utilizando la estrategia institucional **Ruptura Alcista (ORB 15m) + Fair Value Gap (FVG)**.

---

## 📊 Resultados de Backtesting (60 Días, Velas de 5 Minutos)

| Activo | Estrategia | R-Factor | Win Rate | Retorno Neto | Max Drawdown | Profit Factor |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| **Nasdaq (`QQQ`)** | **ORB + FVG** | **2.0** | **37.9%** | **+7.01%** | **7.87%** | **1.22** |
| **Nasdaq (`QQQ`)** | ORB + FVG | 2.5 | 31.0% | +3.57% | 9.92% | 1.13 |
| **S&P 500 (`SPY`)** | ORB + FVG | 2.0 | 17.9% | -23.55% | 27.71% | 0.43 |

> [!NOTE]
> El índice Nasdaq (`QQQ`) es un activo altamente tendencial y de fuerte impulso institucional durante la mañana de Wall Street, lo que permite capturar movimientos limpios de expansión. Por el contrario, el S&P 500 (`SPY`) tiende a presentar mayor reversión a la media, por lo que el bot lo mantiene deshabilitado preventivamente hasta que el auto-optimizador detecte condiciones de mercado favorables.

---

## ⚙️ Características Principales

1. **Monitoreo Multiactivo:** Evalúa simultáneamente `QQQ` y `SPY` durante toda la sesión regular americana (09:30 a 15:55 EST).
2. **Órdenes Bracket OCO en Servidor:** Al detectar una señal, envía órdenes límite de entrada con **Stop Loss** y **Take Profit** adjuntos y gestionados directamente por Alpaca.
3. **Cierre Forzoso Intradía (15:55 EST):** Cancela órdenes pendientes y cierra posiciones antes del cierre de mercado para evitar gaps nocturnos.
4. **Auto-Optimizador Semanal:** Cada domingo a las 00:00 UTC, corre un backtest de los últimos 30 días y auto-calibra los parámetros y estado de cada índice.

---

## 🚀 Configuración en GitHub Actions

Agrega los siguientes secretos en tu repositorio de GitHub (`Settings` -> `Secrets and variables` -> `Actions`):

* `ALPACA_API_KEY`: Tu API Key ID de Alpaca (empieza por `PK...` para Paper Trading).
* `ALPACA_SECRET_KEY`: Tu Secret Key de Alpaca.
* `ALPACA_BASE_URL`: `https://paper-api.alpaca.markets`
