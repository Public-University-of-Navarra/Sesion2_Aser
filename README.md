# Sesión 2 · Arquitectura base

Desarrollo de Equipos Electrónicos · Máster UPNA · Aser Méndez

Placa mínima: entrada de 9 V por bornas → LDO de 3,3 V → microcontrolador STM32G031K8T6 con tres entradas analógicas filtradas (RC paso bajo 1 kΩ / 100 nF, fc ≈ 1,6 kHz), una salida digital y conector SWD.

## Estructura
- Sesion2_Aser.kicad_sch (raíz): J101 (bornas 9 V) y los bloques Alimentacion y Microcontrolador.
- Alimentacion.kicad_sch: U201 MCP1703A-3302E/DB con C201 y C202.
- Microcontrolador.kicad_sch: U301 STM32G031K8T6, J301 (E/S), J302 (SWD), C301 y tres instancias de FiltroRC.kicad_sch.
- Tensiones por pines jerárquicos: VIN (raíz → Alimentacion) y 3V3 (Alimentacion → Microcontrolador). GND común.

## Selección de componentes (Mouser)
| Función | MPN | Fabricante | Motivo |
|---|---|---|---|
| MCU | STM32G031K8T6 | STMicroelectronics | Cortex-M0+, 1,7–3,6 V, LQFP-32, activo |
| LDO 3,3 V | MCP1703A-3302E/DB | Microchip | Hasta 16 V de entrada (9 V con margen), 250 mA, cerámicos de 1 µF |
| Bornas alimentación | 1715721 | Phoenix Contact | 2 polos, paso 5,08 mm |
| Conector SWD | 61300511121 | Würth Elektronik | Tira 1×5, 2,54 mm |
| Conector E/S | 61300611121 | Würth Elektronik | Tira 1×6, 2,54 mm |

## Ramas
- main: estructura e integración
- alimentacion: hoja de alimentación
- microcontrolador: hoja del MCU y BOM