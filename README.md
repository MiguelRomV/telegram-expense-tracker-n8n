# Control de gastos por Telegram

Automatización para registrar gastos desde Telegram y almacenarlos en Notion. El flujo se ejecuta con **n8n**, usa **Ollama** para interpretar mensajes en lenguaje natural y responde al usuario con una confirmación o un resumen diario.

> Proyecto de aprendizaje implementado con acompañamiento guiado de IA. La responsable del repositorio realizó la configuración, integración, pruebas y despliegue siguiendo una guía paso a paso.

## Qué hace

- Recibe mensajes de texto desde un bot de Telegram.
- Valida que el mensaje tenga intención de gasto y un monto.
- Extrae monto, categoría, comercio, fecha y descripción con un modelo local de Ollama.
- Guarda el movimiento en una base de datos de Notion.
- Confirma el registro por Telegram.
- Responde `/hoy` con el total de gastos registrados durante el día.

Ejemplo: `Gasté $250 en gasolina`

## Stack

- n8n
- Telegram Bot API
- Ollama + Qwen 2.5
- Notion API
- Termux en Android

## Despliegue sin cuota de nube

El servidor se configuró en un teléfono Android reutilizado con **Termux**, conectado a Wi‑Fi de forma continua. Así, la automatización puede funcionar sin pagar hosting, servidores administrados ni servicios de nube.

Esto elimina las cuotas de infraestructura; como cualquier servidor doméstico, depende de disponer de electricidad e internet.

## Uso

1. Importa [`workflow/telegram-expense-tracker.template.json`](workflow/telegram-expense-tracker.template.json) en n8n.
2. Crea y asigna tus propias credenciales de Telegram, Ollama y Notion.
3. Reemplaza `YOUR_NOTION_DATABASE_ID` por el ID de tu base de datos de Notion.
4. Asegura que la base tenga propiedades compatibles con el flujo: Descripción, Monto, Moneda, Categoría, SubCategoría, Comercio, Fecha, Tipo, ID Transacción y Procesado.
5. Activa el workflow y prueba desde Telegram.

## Seguridad

La plantilla publicada no incluye tokens, credenciales, IDs de conexiones, webhooks ni datos privados. Cada persona debe configurar sus propias integraciones antes de usarla.

## Licencia

MIT
