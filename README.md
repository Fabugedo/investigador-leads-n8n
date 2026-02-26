# Investigador de Leads – n8n Automation

Automatización desarrollada en n8n que implementa un flujo determinista para investigación de leads.

## 📌 Objetivo

Automatizar el proceso:

Google Sheets (NEW leads)  
→ Validación  
→ Búsqueda / evaluación  
→ Simulación de IA (determinista)  
→ Envío a Slack  
→ Actualización de estado en Google Sheets (DONE / DISCARDED)

---

## 🏗 Arquitectura del flujo

1. Trigger desde Google Sheets
2. Selección de 1 lead con status NEW
3. Validaciones mínimas (nombre, rol, URL)
4. Evaluación de confianza
5. Motor AI simulado (determinista, sin costo)
6. Envío a Slack
7. Actualización de estado final

---

## 🤖 Motor AI

Para evitar costos externos, el nodo `13_ai_engine` implementa:

- Normalización de score (0–1)
- Umbral mínimo de confianza
- Generación de summary_1liner
- Generación de risks_flags
- Determinación final_status_suggested

No utiliza modelos externos.  
El comportamiento es reproducible y controlado.

---

## 📂 Archivos

- `investigador-leads-workflow.json` → Export completo del workflow n8n

---

## 🧠 Características técnicas

- Flujo determinista
- Procesa 1 lead por ejecución
- Control de estado explícito
- Separación de responsabilidades por nodo
- Arquitectura desacoplada
- Simulación de IA reemplazable por modelo real

---

## 🚀 Cómo usar

1. Importar el JSON en n8n
2. Configurar credenciales de Google Sheets
3. Configurar credenciales de Slack
4. Ejecutar workflow

---

## 📌 Estado

Proyecto funcional.
Preparado para reemplazar el motor simulado por IA real si se desea.
